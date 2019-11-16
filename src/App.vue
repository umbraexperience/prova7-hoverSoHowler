<template>
  <div id="app">
    <!--     <div @click="playSound">So CLICK</div>
    <div @mouseover="playSound">So 1</div>
    <p v-show="active">SONA</p> -->

    <div>
      <input
        @input="changeSound"
        type="range"
        v-model="position"
        min="-1"
        max="1"
        step="0.1"
      />
    </div>

    <p>{{ this.position }}</p>
  </div>
</template>

<script>
// eslint-disable-next-line no-unused-vars
import { Howl, Howler } from "howler";

export default {
  name: "app",
  components: {},
  data: function() {
    return {
      position: 0,
      sound: ""
    };
  },
  mounted() {
    this.sound = new Howl({
      src: [
        "https://files.freemusicarchive.org/storage-freemusicarchive-org/music/Oddio_Overplay/Christian_Bjoerklund/Skapmat/Christian_Bjoerklund_-_01_-_Hallon.mp3"
      ]
    });

    this.sound.stereo(0);
    this.sound.pannerAttr({});

    this.sound.play();
  },
  methods: {
    changeSound() {
      console.log(Number(this.position));
      this.sound.stereo(Number(this.position));
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

input {
  width: 100%;
}
</style>
