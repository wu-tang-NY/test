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
          <h5><strong>CX:</strong></h5>
          <vs-slider color="#41b883" v-model="figure.cx" :max="500" />
        </div>
        <div class="col">
          <h5><strong>CY:</strong></h5>
          <vs-slider color="#41b883" v-model="figure.cy" :max="500" />
        </div>
      </div>
      <div class="row params-item">
        <h5><strong>R:</strong></h5>
        <vs-slider color="#41b883" v-model="figure.r" :min="10" :max="150" />
      </div>
      <div class="row params-item">
        <h5><strong>Stroke Width:</strong></h5>
          <vs-slider color="#41b883" v-model="figure.strokeWidth" :max="50" />
      </div>
    </div>
    <div class="col">
      <div class="preview">
        <svg>
          <circle
            :cx="figure.cx + figure.r + figure.strokeWidth"
            :cy="figure.cy + figure.r + figure.strokeWidth"
            :r="figure.r"
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
  name: 'CircleComponent',
  data() {
    return {
      figure: {
        cx: 0,
        cy: 0,
        r: 150,
        stroke: '#000',
        fill: '#41b883',
        strokeWidth: 5,
      },
    };
  },
  computed: {
    code() {
      return `<circle
        cx="${this.figure.cx}"
        cy="${this.figure.cy}"
        r="${this.figure.r}"
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
