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
          <h5><strong>X1:</strong></h5>
          <vs-slider color="#41b883" v-model="figure.x1" :max="300" />
        </div>
        <div class="col">
          <h5><strong>X2:</strong></h5>
          <vs-slider color="#41b883" v-model="figure.x2" :max="300" />
        </div>
      </div>
      <div class="row params-item">
        <div class="col">
          <h5><strong>y1:</strong></h5>
          <vs-slider color="#41b883" v-model="figure.y1" :min="50" :max="300" />
        </div>
        <div class="col">
          <h5><strong>y2:</strong></h5>
          <vs-slider color="#41b883" v-model="figure.y2" :min="50" :max="300" />
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
          <line
            :x1="figure.x1"
            :x2="figure.x2"
            :y1="figure.y1"
            :y2="figure.y2"
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
  name: 'LineComponent',
  data() {
    return {
      figure: {
        x1: 50,
        x2: 250,
        y1: 150,
        y2: 150,
        stroke: '#000',
        fill: '#41b883',
        strokeWidth: 5,
      },
    };
  },
  computed: {
    code() {
      return `<line
        x1="${this.figure.x1}"
        x2="${this.figure.x2}"
        y1="${this.figure.y1}"
        y2="${this.figure.y2}"
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
