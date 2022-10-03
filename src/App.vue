<template>
  <div class="edw" id="mountNode"></div>
</template>
<script>
import G6 from "@antv/g6";
const data1 = {
  nodes: [
    { id: "0", label: "0" },
    { id: "1", label: "1" },
    { id: "2", label: "2" },
  ],
  edges: [
    { source: "0", target: "1" },
    { source: "0", target: "2" },
  ],
};
export default {
  data() {
    return {
      // G6实例
      graph: null,
      // 渲染的节点数据
      data: {
        nodes: [
          { id: "0", label: "0" },
          { id: "1", label: "1" },
          { id: "2", label: "2" },
          { id: "3", label: "3" },
          { id: "4", label: "4" },
        ],
        edges: [
          { source: "0", target: "1" },
          { source: "0", target: "2" },
          { source: "0", target: "3" },
          { source: "0", target: "4" },
          { source: "1", target: "2" },
          { source: "1", target: "3" },
        ],
      },
    };
  },
  mounted() {
    // 获取数据webpack://front_cloudbrain_portal/node_modules/@antv/g6-core/es/item/item.js?425b
    this.initG6();
  },
  methods: {
    // 渲染图形
    initG6() {
      const container = document.getElementById("mountNode");
      const width = container.scrollWidth;
      const height = container.scrollHeight;
      this.graph = new G6.Graph({
        container: "mountNode", // String | HTMLElement，必须，容器 id 或容器本身
        width, // Number，必须，图的宽度
        height, // Number，必须，图的高度
        animate: true, // Boolean，可选，切换布局时是否使用动画过度
      });
      // 读取数据和渲染
      this.graph.data(this.data);
      this.graph.render();
      setTimeout(() => {
        console.log(1);
        this.graph.changeData(data1);
      }, 12000);
    },
  },
};
</script>

<style scoped>
.edw {
  width: 100%;
  height: 800px;
  background: rgba(255, 255, 255, 0.3);
}
</style>
