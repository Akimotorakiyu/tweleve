<template>
    <div class="group">
        <h1>钢琴</h1>
        <!-- <div>
                    <button 
                    :class="{'white': (n%2) == 0, 'black': (n%2) == 1}" 
                    :key="n" v-for="n in 12" 
                    :style="{left: 30*n + 'px'}"></button>
                </div> -->
        <div>
            <div>
                <button :class="{'white': ((n+1)%2) == 0, 'black': (n%2) == 0}" :key="n" v-for="n in 89" :style="{left: position(n)}" @click="play(n-1)"></button>
            </div>
        </div>
    </div>
</template>

<script>
import { notes } from "../notes.js";
const prefix = "data:audio/mpeg;base64,";

export default {
  methods: {
    position: function(n) {
      let nPos = 0;
      if (n % 2 == 0) {
        nPos = n / 2;
        return 30 * nPos + 20 + "px";
      } else {
        nPos = (n + 1) / 2;
        return 30 * nPos + "px";
      }
    },
    play(index) {
            var audio = new Audio(prefix + notes[index]);
            audio.play();
        },
  },
   
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
button {
  flex: 1;
  border: 1px solid #7c7c7c;
  outline: 0;
  padding: 0;
  margin: 0;
  position: absolute;
}
.white:active,
.white.active {
  background: #ececec;
}
.white {
  width: 30px;
  background: #fff;
  height: 200px;
  z-index: -1;
}
.black:active,
.black.active {
  background: #404040;
}
.black {
  width: 20px;
  background: #000;
  height: 130px;
}
</style>