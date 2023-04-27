<template>
  <div id="app">
    <MdPreview v-model="mdValue" />
  </div>
</template>

<script>
import MdPreview from "./md-preview/index.vue";

export default {
  name: "App",
  components: {
    MdPreview,
  },
  data() {
    return {
      mdValue: "",
      // mdValue:
        // "# markdown测试文档1\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n![网图](https://images.shejidaren.com/wp-content/uploads/2014/07/free-photos.jpg)\n\n# 进阶版编辑器\n## markdown测试文档2\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n#进阶版编辑器\n```javascript\nexport default defineComponent({\n name: 'MdEditor',\n props: {\n value: {\n type: String,\n default: ''\n }\n },\n setup(props) {\n return () => (\n <MdEditor v-model={[props.value,'modelValue']} />\n );\n }\n});\n```\n\n### markdown测试文档3\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n#进阶版编辑器\n#### markdown测试文档4\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n#进阶版编辑器\n##### markdown测试文档511111111\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n#进阶版编辑器\n###### markdown测试文档6# markdown测试文档1\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n![网图](https://images.shejidaren.com/wp-content/uploads/2014/07/free-photos.jpg)\n\n# 进阶版编辑器\n## markdown测试文档2\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n#进阶版编辑器\n```javascript\nexport default defineComponent({\n name: 'MdEditor',\n props: {\n value: {\n type: String,\n default: ''\n }\n },\n setup(props) {\n return () => (\n <MdEditor v-model={[props.value,'modelValue']} />\n );\n }\n});\n```\n\n## markdown测试文档3\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n#进阶版编辑器\n## markdown测试文档4\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n#进阶版编辑器\n## markdown测试文档5\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n#进阶版编辑器\n## markdown测试文档6",
    };
  },
  mounted() {
    setTimeout(() => {
      this.mdValue =
        "# markdown测试文档1\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n$$\nlkasdjsdlkfj\ndsfksdjf\n$$\n\n:grinning:\n[点击跳转](#jump)\n```mermaid\nflowchart TD \n  Start --> Stop\n```\n\n| 表头| 标题|\n| - | - |\n| 闪电发货就| 闪电发货就|\n| 快速的房间| 快乐多发几个|\n\n![](http://image.res.meizu.com/image/open/ce3417fbf98d42428ccfcbcf5428c397z)\n\n![御堂筋](http://image.res.meizu.com/image/open/4fc2dcac91ad4136801d55fe271af8fez)\n\n![网图](https://images.shejidaren.com/wp-content/uploads/2014/07/free-photos.jpg)\n\n#进阶版编辑器\n## markdown测试文档2\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n#进阶版编辑器\n```javascript\nexport default defineComponent({\n  name: 'MdEditor',\n  props: {\n    value: {\n      type: String,\n      default: ''\n    }\n  },\n  setup(props) {\n    return () => (\n      <MdEditor v-model={[props.value,'modelValue']} />\n    );\n  }\n});\n```\n\n### markdown测试文档3\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n#进阶版编辑器\n![](http://image.res.meizu.com/image/open/f8de36c6a21c4ef8b1dc8ce673746bacz)\n\n#### markdown测试文档4\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n![](http://image.res.meizu.com/image/open/c9077b8f2d0d418ebe7747e68c3ac213z)\n\n#进阶版编辑器\n##### markdown测试文档5\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n![](http://image.res.meizu.com/image/open/a0e819cced36453ba1222b184e9afb53z)\n<span id=\"jump\">跳转到的地方</span>\n#进阶版编辑器\n###### markdown测试文档6![](undefined)\n```mermaidgraph LR\nA --- B\nB-->C[fa:fa-ban forbidden]\nB-->D(fa:fa-spinner);\n```";
    }, 1000);
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
