<template>
  <div id="app">
    <div class="app-controls">
      <button class="btn btn-prev" @click.prevent="onPrevSlide()" v-if="currentSlide > 0">
        <svg xmlns="http://www.w3.org/2000/svg" height="40" viewBox="0 0 24 24" width="24"><path d="M15.41 7.41L14 6l-6 6 6 6 1.41-1.41L10.83 12z" fill="currentColor"/><path d="M0 0h24v24H0z" fill="none"/></svg>
      </button>
      <button class="btn btn-next" @click.prevent="onNextSlide()" v-if="currentSlide + 1 < slides.length">
        <svg xmlns="http://www.w3.org/2000/svg" height="40" viewBox="0 0 24 24" width="24"><path d="M10 6L8.59 7.41 13.17 12l-4.58 4.59L10 18l6-6z" fill="currentColor"/><path d="M0 0h24v24H0z" fill="none"/></svg>
      </button>
    </div>

    <div class="container">
      <h1 class="component-title">{{ slides[currentSlide].label }}</h1>
      <component :is="slides[currentSlide].component"></component>
    </div>
  </div>
</template>

<script>
import RectComponent from './components/rect.vue';
import CircleComponent from './components/circle.vue';
import EllipseComponent from './components/ellipse.vue';
import LineComponent from './components/line.vue';
import PolylineComponent from './components/polyline.vue';
import PolygonComponent from './components/polygon.vue';
import PathComponent from './components/path.vue';

export default {
  name: 'App',
  data() {
    return {
      slides: [{
        label: 'Rectangle',
        component: 'RectComponent',
      }, {
        label: 'Circle',
        component: 'CircleComponent',
      }, {
        label: 'Ellipse',
        component: 'EllipseComponent',
      }, {
        label: 'Line',
        component: 'LineComponent',
      }, {
        label: 'Polyline',
        component: 'PolylineComponent',
      }, {
        label: 'Polygon',
        component: 'PolygonComponent',
      }, {
        label: 'Path',
        component: 'PathComponent',
      }],
      currentSlide: 0,
    };
  },
  components: {
    RectComponent,
    EllipseComponent,
    CircleComponent,
    LineComponent,
    PolylineComponent,
    PolygonComponent,
    PathComponent,
  },
  methods: {
    onNextSlide() {
      this.currentSlide = this.currentSlide >= this.slides.length ? 0 : this.currentSlide + 1;
    },
    onPrevSlide() {
      this.currentSlide = this.currentSlide.length <= 0 ? this.slides.length - 1 : this.currentSlide - 1;
    },
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding: 60px 0;
  min-height: 100vh;
  display: flex;
}

.container {
  max-width: 1200px;
  width: 100%;
  margin: 0 auto;
  padding: 0 50px;
  flex: 1;
  display: flex;
  flex-direction: column;
}

.component {
  display: flex;
  flex: 1;
}

.component .col {
  width: 100%;
}

.component-title {
  margin: 0 auto 50px;
  font-weight: 900;
  font-size: 60px;
}

.app-controls .btn {
  border: none;
  border-radius: 0;
  box-shadow: none;
  position: fixed;
  top: 0;
  bottom: 0;
  width: 120px;
  font-size: 30px;
  color: rgba(0,0,0, .75);
  outline: none;
  transition: .25s ease-in-out;
}

.app-controls .btn:hover {
  background-color: rgba(0, 0, 0, .05);
}

.btn-prev {
  left: 0;
}

.btn-next {
  right: 0;
}

.preview {
  height: 100%;
  display: flex;
  justify-content: flex-end;
  padding-left: 150px;
}

svg {
  width: 100%;
}

.params {
  text-align: left;
}

.params-item {
  border-bottom: 1px dashed rgba(0,0,0, .25);
  padding-top: 20px;
  padding-bottom: 20px;
}

.params-item > .col {
  padding: 0;
}

.params-item > .col + .col {
  padding-left: 30px;
}

.params-item h5 {
  font-size: 18px;
}

.component-code {
  background-color: #eee;
  border-radius: 4px;
  padding: 16px 20px;
  margin-bottom: 40px;
}

.con-vs-slider {
  min-width: 100px;
}

input[type="color"] {
  width: 100%;
}
</style>
