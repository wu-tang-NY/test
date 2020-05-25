<template>
  <div class="component">
    <div class="col params">
      <div class="row">
        <code class="component-code">
          {{ code }}
        </code>
      </div>
      <div class="row">
        <h3><strong>Attributes:</strong></h3>
      </div>
      <div class="row params-item">
        <div class="col">
          <h5><strong>Fill:</strong></h5>
          <input type="color" v-model="figure.fill" name="" >
        </div>
        <div class="col">
          <h5><strong>Stroke:</strong></h5>
          <input type="color" v-model="figure.stroke" name="" >
        </div>
      </div>
      <div class="row params-item">
        <h5><strong>Stroke Width:</strong></h5>
        <vs-slider color="#41b883" v-model="figure.strokeWidth" :max="50" />
      </div>
    <div class="row" style="margin-top: 30px">
      <h5><strong>Options:</strong></h5>
    </div>
    <div class="row params-item">
      <div class="col">
        <h5><strong>Sides:</strong></h5>
        <vs-slider color="#41b883" v-model="sides" :max="50" />
      </div>
      <div class="col">
      <h5><strong>Minimum radius:</strong></h5>
      <vs-slider color="#41b883" v-model="minRadius" :max="50" />
      </div>
    </div>
    </div>
    <div class="col">
      <div class="preview">
        <svg>
          <polygon :points="points" :fill="figure.fill" :stroke="figure.stroke" :stroke-width="figure.strokeWidth" />
        <circle cx="100" cy="100" r="90" fill="none" stroke="#35495e"></circle>
        </svg>
      </div>
    </div>
  </div>
</template>

<script>
import { TweenLite } from 'gsap'
// import 'gsap/CSSPlugin'

function valueToPoint(value, index, total) {
  var x = 0;
  var y = -value * 0.9;
  var angle = ((Math.PI * 2) / total) * index;
  var cos = Math.cos(angle);
  var sin = Math.sin(angle);
  var tx = x * cos - y * sin + 100;
  var ty = x * sin + y * cos + 100;
  return { x: tx, y: ty };
}

function generatePoints(stats) {
  var total = stats.length;
  return stats
    .map(function(stat, index) {
      var point = valueToPoint(stat, index, total);
      return point.x + "," + point.y;
    })
    .join(" ");
}


export default {
  name: 'PolygonComponent',
  data() {
    var defaultSides = 10;
    var stats = Array.apply(null, { length: defaultSides }).map(
      function() {
        return 100;
      }
    );
    return {
      stats: stats,
      points: generatePoints(stats),
      sides: defaultSides,
      minRadius: 50,
      interval: null,
      updateInterval: 500,
      figure: {
        stroke: '#000',
        fill: '#41b883',
        strokeWidth: 0,
      },
    };
  },
  computed: {
    code() {
      return `<polygon
        points="50 160 55 180 70 180 60 190 65 205 50 195 35 205 40 190 30 180 45 180"
        stroke="${this.figure.stroke}"
        fill="${this.figure.fill}"
        stroke-width="${this.figure.strokeWidth}"
      />`;
    },
  },
  watch: {
    sides: function(newSides, oldSides) {
      var sidesDifference = newSides - oldSides;
      if (sidesDifference > 0) {
        for (let i = 1; i <= sidesDifference; i++) {
          this.stats.push(this.newRandomValue());
        }
      } else {
        var absoluteSidesDifference = Math.abs(sidesDifference);
        for (let i = 1; i <= absoluteSidesDifference; i++) {
          this.stats.shift();
        }
      }
    },
    stats: function(newStats) {
      TweenLite.to(this.$data, this.updateInterval / 1000, {
        points: generatePoints(newStats)
      });
    },
    updateInterval: function() {
      this.resetInterval();
    }
  },
  mounted() {
    this.resetInterval();
  },
  methods: {
    randomizeStats: function() {
      var vm = this;
      this.stats = this.stats.map(function() {
        return vm.newRandomValue();
      });
    },
    newRandomValue: function() {
      return Math.ceil(
        this.minRadius + Math.random() * (100 - this.minRadius)
      );
    },
    resetInterval: function() {
      var vm = this;
      clearInterval(this.interval);
      this.randomizeStats();
      this.interval = setInterval(function() {
        vm.randomizeStats();
      }, this.updateInterval);
    }
  }
};
</script>

<style lang="scss" scoped>

</style>
