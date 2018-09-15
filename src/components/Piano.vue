<template>
    <div class="group">
        <h1>Rainbow Piano</h1>
        <h5>Silver Research</h5>
        <div>
            <div>
                <button :class="{ 'black': (n%2) == 0,'white1': ((n+1)/2)%6==1,'white2': ((n+1)/2)%6==2,'white3': ((n+1)/2)%6==3,'white4': ((n+1)/2)%6==4,'white5': ((n+1)/2)%6==5,'white6': ((n+1)/2)%6==0,}" 
                :key="n" v-for="n in 89" :style="{left: position(n)}" @click="play(n-1)"></button>
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
  border: 1px solid #fff;
  outline: 0;
  padding: 0;
  margin: 0;
  position: absolute;
}
.black:active,
.black.active {
  background: #404040;
}
.black {
  width: 20px;
  background: #333;
  height: 130px;
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
/* colorfull */
.white1:active,
.white1.active {
  background: #ececec;
}
.white1 {
  width: 30px;
  background: #ffcccc;
  height: 200px;
  z-index: -1;
}
.white2:active,
.white2.active {
  background: #ececec;
}
.white2 {
  width: 30px;
  background: #ffffcc;
  height: 200px;
  z-index: -1;
}
.white3:active,
.white3.active {
  background: #ececec;
}
.white3 {
  width: 30px;
  background: #ccffcc;
  height: 200px;
  z-index: -1;
}
.white4:active,
.white4.active {
  background: #ececec;
}
.white4 {
  width: 30px;
  background: #ccffff;
  height: 200px;
  z-index: -1;
}
.white5:active,
.white5.active {
  background: #ececec;
}
.white5 {
  width: 30px;
  background: #ccccff;
  height: 200px;
  z-index: -1;
}
.white6:active,
.white6.active {
  background: #ececec;
}
.white6 {
  width: 30px;
  background: #ffccff;
  height: 200px;
  z-index: -1;
}




</style>