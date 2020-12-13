<template>
  <div id="mountNode" :style="{width:width}">
    <div class="editor" >
      <div style="height: 42px;"></div>
      <div class="bottom-container">      
        <page :height="height" :width="width"  :data="data" />
      </div>
    </div>
  </div>
</template>
<script>
import Page from "../Page";
export default {
  name: "G6ETL",
  components: {
    Page
  },
  props: {
    height: {
      type: Number,
      default: document.documentElement.clientHeight
    },
    width: {
      type: Number,
      default: document.documentElement.clientWidth
    },
    data: {
      type: Object,
      default: () => {}
    }
  },
  created() {
    this.init();
  },
  data() {
    return {
    };
  },
  methods: {
    init() {
    }
  }
};
</script>

<style scoped>
.editor {
  position: relative;
  width: 100%;
  user-select: none;
  -moz-user-select: none;
  -webkit-user-select: none;
  -ms-user-select: none;
}
.bottom-container {
  position: relative;
}
</style>