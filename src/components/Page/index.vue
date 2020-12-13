<template>
  <div class="page">
    <div :id="pageId" class="graph-container" style="position: relative;"></div>
  </div>
</template>


<script>
import G6  from "@antv/g6";
export default {
  data() {
    return {
      pageId: "graph-container",
      graph: null
    };
  },
  props: {
    height: {
      type: Number,
      default: 0
    },
    width: {
      type: Number,
      default: 0
    },
    data: {
      type: Object,
      default: () => {}
    }
  },
  created() {
  },
  mounted() {
    this.$nextTick(() => {
      this.init();
    });
  },
  methods: {
    init() {
      const height =  this.height - 42 
      const width =  this.width - 200
      this.Grid = new G6.Grid()
      this.graph = new G6.Graph({
        container: "graph-container",
        height: height,
        width: width,
        modes: {
          // 支持的 behavior
          default: [
            "drag-canvas",
            "zoom-canvas",
            "hover-node",
            "select-node",
            "hover-edge",
            "keyboard",
            "customer-events",
            "add-menu"
          ]
        },
        defaultNode: {         
          type: 'modelRect',        // 节点样式配置         
          size: [240, 40],  // 节点大小  modelRect的size 为数组
          style: {
            fill: '#f0f5ff',
            stroke: '#adc6ff',
            lineWidth: 2,
          },
          // 节点上的标签文本配置
          labelCfg: {
            // 节点上的标签文本样式配置
            style: {
              fill: '#9254de', // 节点标签文字颜色
              fontSize: 18,
            },
          },
          //指定 modelRect 周围「上、下、左、右」四个小圆点
          linkPoints: {
            top: true,
            bottom: true,
            left: false,
            right: false,
            size: 5,
            fill: '#fff',
          },
          //指定连接点
          anchorPoints: [
            [0.5, 0],
            [0.5, 1],
          ],
        },
        // 边在默认状态下的样式配置（style）和其他配置
        defaultEdge: {
          type: 'cubic-vertical',
          // ...                 // 边的其他配置
          // 边样式配置
          style: {
            opacity: 0.6, // 边透明度
            stroke: 'grey', // 边描边颜色
            endArrow: true,
          },
          // 边上的标签文本配置
          labelCfg: {
            autoRotate: true, // 边上的标签文本根据边的方向旋转
          },
        },
        layout: {
          type: 'dagre',
          rankdir: 'BT', // 可选，默认为图的中心
          align: 'DL', // 可选
          nodesep: 20, // 可选
          ranksep: 50, // 可选
          controlPoints: true, // 可选
        },
      });
      const initData = {// 点集
            nodes: [
            {
                id: 'node1', // String，该节点存在则必须，节点的唯一标识
                label: 'last'  
            },
            {
                id: 'node2', // String，该节点存在则必须，节点的唯一标识
                label: 'las1'  
            },
            {
                id: 'node3', // String，该节点存在则必须，节点的唯一标识
                label: 'last1-1'  
            },
            {
                id: 'node4', // String，该节点存在则必须，节点的唯一标识
                label: 'last2',  
                style: {
                  fill: '#FF4500',
                  stroke: '#adc6ff',
                  lineWidth: 2,
                },
            },
            {
                id: 'node5', // String，该节点存在则必须，节点的唯一标识
                label: 'last2-1'  
            },
            {
                id: 'node6', // String，该节点存在则必须，节点的唯一标识
                label: 'last2-3'  
            },
            ],
            // 边集
            edges: [
            {
                source: 'node2', // String，必须，起始点 id
                target: 'node1', // String，必须，目标点 id
                style: {opacity: 0.6, // 边透明度
                        stroke: 'red',
                        endArrow: true,
                      }, // 边描边颜色
            },
            {
                source: 'node3', // String，必须，起始点 id
                target: 'node1', // String，必须，目标点 id

            },
            {
                source: 'node4', // String，必须，起始点 id
                target: 'node2', // String，必须，目标点 id
                 style: {opacity: 0.6, // 边透明度
                        stroke: 'red',
                        endArrow: true,
                      }, // 边描边颜色
            },
            {
                source: 'node5', // String，必须，起始点 id
                target: 'node3', // String，必须，目标点 id
                style: {opacity: 0.6, // 边透明度
                        stroke: 'red',
                        endArrow: true,
                      }, // 边描边颜色
            },
            {
                source: 'node6', // String，必须，起始点 id
                target: 'node3', // String，必须，目标点 id
            },
            ]
      }
      this.graph.data(initData)
      this.graph.render();
    },
  }
};
</script>

<style scoped>
.page{
  margin-left:200px;
  margin-right: 200px;
}
</style>