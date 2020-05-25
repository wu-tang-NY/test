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
        <div class="col">
          <h5><strong>Y:</strong></h5>
          <vs-slider color="#41b883" v-model="figure.y" :max="500" />
        </div>
      </div>
      <div class="row params-item">
        <div class="col">
          <h5><strong>RX:</strong></h5>
          <vs-slider color="#41b883" v-model="figure.rx" :max="50" />
        </div>
        <div class="col">
          <h5><strong>RY:</strong></h5>
          <vs-slider color="#41b883" v-model="figure.ry" :max="50" />
        </div>
      </div>
      <div class="row params-item">
        <div class="col">
          <h5><strong>Width:</strong></h5>
          <vs-slider color="#41b883" v-model="figure.width" :min="50" :max="400" />
        </div>
        <div class="col">
          <h5><strong>Height:</strong></h5>
          <vs-slider color="#41b883" v-model="figure.height" :min="50" :max="400" />
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
          <rect
            :x="figure.x + figure.strokeWidth / 2"
            :y="figure.y + figure.strokeWidth / 2"
            :rx="figure.rx"
            :ry="figure.ry"
            :width="figure.width"
            :height="figure.height"
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
  name: 'RectComponent',
  data() {
    return {
      figure: {
        x: 0,
        y: 0,
        rx: 0,
        ry: 0,
        width: 200,
        height: 400,
        stroke: '#000',
        fill: '#41b883',
        strokeWidth: 5,
      },
    };
  },
  computed: {
    code() {
      return `<rect
        x="${this.figure.x}"
        y="${this.figure.y}"
        rx="${this.figure.rx}"
        ry="${this.figure.ry}"
        width="${this.figure.width}"
        height="${this.figure.height}"
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
