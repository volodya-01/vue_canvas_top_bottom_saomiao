<template>
  <div class="cover">
    <canvas ref="coverflag"></canvas>
  </div>
</template>

<script>
export default {
  name: "cover2",
  data() {
    return {
      timerval: null,
      i: 0,
      logtime: 0
    };
  },
  mounted() {
    this.timer();
  },
  methods: {
    timer() {
      this.i++;
      let canvas = this.$refs.coverflag;
      canvas.width = document.body.clientWidth;
      canvas.height = document.body.clientHeight;

      let ctx = canvas.getContext("2d");
      ctx.clearRect(0, 0, canvas.width, canvas.height);

      this.drawcover(ctx, this.i);
      cancelAnimationFrame(this.timerval); //清除帧动画
      this.timerval = window.requestAnimationFrame(this.timer);
    },
    drawcover(ctx, i) {
      ctx.save();
      ctx.fillStyle = "rgba(255,0,0,0.3)";
      if (i < this.$refs.coverflag.height) {
        ctx.beginPath();
        ctx.fillRect(0, 0, this.$refs.coverflag.width, i);
        ctx.closePath();
        ctx.beginPath();
        ctx.moveTo(0, i);
        ctx.lineTo(this.$refs.coverflag.width, i);
        ctx.strokeStyle = "red";
        ctx.lineWidth = 5;
        ctx.stroke();
        ctx.closePath();
      } else {
        this.i = 0;
        this.$refs.coverflag.height = 0;
        ctx.clearRect(
          0,
          0,
          this.$refs.coverflag.width,
          this.$refs.coverflag.height
        );
      }

      ctx.closePath();
      ctx.restore();
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import "@/styles/global.scss";
.cover {
  display: flex;
  flex-flow: column;
  justify-content: flex-start;
  align-items: flex-start;
  width: vw(1920);
  height: vh(1080);
  //background-color: #42b983;
  overflow: hidden;
}
</style>
