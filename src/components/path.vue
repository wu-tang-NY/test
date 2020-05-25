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
          <input type="color" v-model="rect.fill" name="" >
        </div>
        <div class="col">
          <h5><strong>Stroke:</strong></h5>
          <input type="color" v-model="rect.stroke" name="" >
        </div>
      </div>
      <div class="row params-item">
        <div class="col">
          <h5><strong>X:</strong></h5>
          <vs-slider color="#41b883" v-model="rect.x" :max="500" />
        </div>
        <div class="col">
          <h5><strong>Y:</strong></h5>
          <vs-slider color="#41b883" v-model="rect.y" :max="500" />
        </div>
      </div>
      <div class="row params-item">
        <div class="col">
          <h5><strong>Width:</strong></h5>
          <vs-slider color="#41b883" v-model="rect.width" :min="50" :max="400" />
        </div>
        <div class="col">
          <h5><strong>Height:</strong></h5>
          <vs-slider color="#41b883" v-model="rect.height" :min="50" :max="400" />
        </div>
      </div>
      <div class="row params-item">
        <h5><strong>Stroke Width:</strong></h5>
          <vs-slider color="#41b883" v-model="rect.strokeWidth" :max="50" />
      </div>
    </div>
    <div class="col">
      <div class="preview">
        <svg>
          <rect
            :x="rect.x + rect.strokeWidth / 2"
            :y="rect.y + rect.strokeWidth / 2"
            :width="rect.width"
            :height="rect.height"
            :stroke="rect.stroke"
            :fill="rect.fill"
            :stroke-width="rect.strokeWidth"
          />
        </svg>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PathComponent',
  data() {
    return {
      figure: {
        x: 0,
        y: 0,
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
        x="${this.rect.x}"
        y="${this.rect.y}"
        width="${this.rect.width}"
        height="${this.rect.height}"
        stroke="${this.rect.stroke}"
        fill="${this.rect.fill}"
        stroke-width="${this.rect.strokeWidth}"
      />`;
    },
  },
};
</script>

<style lang="scss" scoped>

</style>
