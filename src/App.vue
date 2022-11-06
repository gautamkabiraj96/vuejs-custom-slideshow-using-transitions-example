<template>
  <div id="app">
    <button @click="displayPreviousSlide" class="slider-btn">Previous</button>
    <button @click="displayNextSlide" class="slider-btn">Next</button>
    <transition name="slide-fade" mode="out-in">
      <div :key="selectedImage">
        <img :src="selectedImage" />
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      urls: [
        "https://picsum.photos/id/39/700/300",
        "https://picsum.photos/id/49/700/300",
        "https://picsum.photos/id/65/700/300",
      ],
      selectedImage: null,
      imageIndex: 0,
    };
  },
  mounted() {
    this.selectedImage = this.urls[0];
  },
  methods: {
    displayNextSlide() {
      if (this.imageIndex < this.urls.length - 1) {
        this.imageIndex++;
      } else {
        this.imageIndex = 0;
      }
      this.selectedImage = this.urls[this.imageIndex];
    },
    displayPreviousSlide() {
      if (this.imageIndex > 0) {
        this.imageIndex--;
      } else {
        this.imageIndex = this.urls.length - 1;
      }
      this.selectedImage = this.urls[this.imageIndex];
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #000000;
  margin: 40px;
}
.slide-fade-enter-active {
  transition: all 0.25s ease;
}

.slide-fade-leave-active {
  transition: all 0.25s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter,
.slide-fade-leave-to {
  transform: scale(0.95);
  opacity: 0;
}

.slider-btn {
  margin-bottom: 1em;
  background: rgb(41, 41, 41);
  color: #fff;
  border: none;
  padding: 8px 12px;
  cursor: pointer;
  min-width: 100px;
  margin: 2em 0.5em;
}
</style>
