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
          <vs-slider color="#41b883" v-model="figure.x" :max="500" />
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
          <polyline
            :points="figure.points"
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
  name: 'PolylineComponent',
  data() {
    return {
      figure: {
        points: '60 110, 65 120, 70 115, 75 130, 80 125, 85 140, 90 135, 95 150, 100 145',
        stroke: '#000',
        fill: '#41b883',
        strokeWidth: 5,
      },
    };
  },
  computed: {
    code() {
      return `<polyline
        points="${this.figure.points}"
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
