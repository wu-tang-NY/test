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
        <div class="col">
          <h5><strong>X:</strong></h5>
          <vs-slider color="#41b883" v-model="figure.cx" :max="500" />
        </div>
        <div class="col">
          <h5><strong>Y:</strong></h5>
          <vs-slider color="#41b883" v-model="figure.cy" :max="500" />
        </div>
      </div>
      <div class="row params-item">
        <div class="col">
          <h5><strong>RX:</strong></h5>
          <vs-slider color="#41b883" v-model="figure.rx" :min="10" :max="200" />
        </div>
        <div class="col">
          <h5><strong>RY:</strong></h5>
          <vs-slider color="#41b883" v-model="figure.ry" :min="10" :max="200" />
        </div>
      </div>
      <div class="row params-item">
        <h5><strong>Stroke Width:</strong></h5>
          <vs-slider color="#41b883" v-model="figure.strokeWidth" :max="50" />
      </div>
    </div>
    <div class="col">
      <div class="preview">
        <svg>
          <ellipse
            :cx="figure.cx + figure.rx + figure.strokeWidth"
            :cy="figure.cy + figure.ry + figure.strokeWidth"
            :rx="figure.rx"
            :ry="figure.ry"
            :stroke="figure.stroke"
            :fill="figure.fill"
            :stroke-width="figure.strokeWidth"
          />
        </svg>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'EllipseComponent',
  data() {
    return {
      figure: {
        cx: 0,
        cy: 0,
        rx: 100,
        ry: 200,
        stroke: '#000',
        fill: '#41b883',
        strokeWidth: 5,
      },
    };
  },
  computed: {
    code() {
      return `<ellipse
        cx="${this.figure.cx}"
        cy="${this.figure.cy}"
        rx="${this.figure.ry}"
        ry="${this.figure.ry}"
        stroke="${this.figure.stroke}"
        fill="${this.figure.fill}"
        stroke-width="${this.figure.strokeWidth}"
      />`;
    },
  },
};
</script>

<style lang="scss" scoped>

</style>
