<template>
  <div class="hello">
    <cover2/>
  </div>
</template>

<script>
import cover2 from './cover2'
export default {
  name: "HelloWorld",
  components:{
    cover2
  },
  data() {
    return {};
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
@import "@/styles/global.scss";
.hello{
   display: flex;
  flex-flow: column;
  justify-content: flex-start;
  align-items: flex-start;
  width: vw(1920);
  height: vh(1080);
  overflow: hidden;
}
a {
  color: #42b983;
  color: #2c3e50;
}
</style>
