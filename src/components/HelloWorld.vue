<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <el-button type="success">{{ name }}</el-button>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive, toRefs } from "vue";

export default defineComponent({
  name: "HelloWorld",
  props: {
    msg: String,
  },
  setup(props, ctx) {
    console.log("ctx: ", ctx);
    console.log("props: ", props);
    const state = reactive({
      name: "test",
    });

    return {
      ...toRefs(state),
    };
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
