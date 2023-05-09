<!--
 * @Author: ZtrainWilliams ztrain1224@163.com
 * @Date: 2023-04-26 19:43:44
 * @Description: 
-->
<template>
  <div id="app">
    <el-tabs v-model="activeName" class="demo-tabs">
      <el-tab-pane label="MdPreview" name="MdPreview">
        <MdPreview v-model="mdValue" />
      </el-tab-pane>
      <el-tab-pane label="HTMLMdPreview" name="HTMLMdPreview">
        <HTMLMdPreview v-model="htmlValue" />
      </el-tab-pane>
    </el-tabs>
  </div>
</template>

<script>
import MdPreview from "./md-preview/index.vue";
import HTMLMdPreview from "./md-preview/HtmlPreview.vue";

export default {
  name: "App",
  components: {
    MdPreview,
    HTMLMdPreview,
  },
  data() {
    return {
      activeName: "HTMLMdPreview",
      htmlValue:
        '<h1><span dir="ltr">11111111</span></ a></code></tt></span></h1>\n\n<p><a id="1" name="1">1.集成文档</ a></p >\n\n<p>&nbsp; &nbsp; &nbsp; &nbsp;CKEditor 即 FCKEDITOR 。FCKeditor是目前最优秀的可见即可得网页编辑器之一，它采用JavaScript编写。具备功能强大、配置容易、跨浏览器、支持多种编程语言、开源等特点。它非常流行，互联网上很容易找到相关技术文档，国内许多WEB项目和大型网站均采用了FCKeditor。</p >\n\n<p>随着CKEditor4.4.1的发布，以前一直困扰的代码高亮问题终于完美的得到解决，在CKEditor4.4中官方发布了Code Snippet这个代码片段的插件，终于可以完美的内嵌使用代码高亮了，以前都是使用网友自己开发的代码高亮插件。下面就来介绍如何使用Code Snippet这个代码高亮插件。本文还介绍了CKEditor中如何安装Code Snippet插件。</p >\n\n<p>CKEditor 即 FCKEDITOR 。FCKeditor是目前最优秀的可见即可得网页编辑器之一，它采用JavaScript编写。具备功能强大、配置容易、跨浏览器、支持多种编程语言、开源等特点。它非常流行，互联网上很容易找到相关技术文档，国内许多WEB项目和大型网站均采用了FCKeditor。</p >\n\n<p>随着CKEditor4.4.1的发布，以前一直困扰的代码高亮问题终于完美的得到解决，在CKEditor4.4中官方发布了Code Snippet这个代码片段的插件，终于可以完美的内嵌使用代码高亮了，以前都是使用网友自己开发的代码高亮插件。下面就来介绍如何使用Code Snippet这个代码高亮插件。本文还介绍了CKEditor中如何安装Code Snippet插件。</p >\n\n<pre>\n<code>getExternalDocDetail () {\n this.$axios\n .get(api.getExternalDocDetail, {\n params: {\n id: this.$route.query.id\n }\n })\n .then(res =&gt; {\n this.docDetail = res.data.value\n if(this.docDetail !== null) {\n this.status = true\n }\n })\n },</code></pre>\n\n<p><a id="2" name="2">2.初始化sdk</ a></p >\n\n<p>Code Snippet是CKEditor4.4.1的新插件，主要提供添加代码片段高亮显示的功能。另外注意一点的是，Code Snippet只是作为CKEditor的插件，真正实现代码高亮的是highlight.js这个代码高亮JS库。</p >\n\n<p>Code Snippet只是将highlight.js作为默认的高亮库,由于highlight.js已经集成在Code Snippet中，所以我们在使用CKEditor时候是不需要另外再引用highlight.js这个库。（< a href="http://highlightjs.org/" target="_blank">点击这里查看highlight.js的官方网站</ a>）。</p >\n\n<p>< img alt="" height="194" src="http://image.res.meizu.com/image/open/14c6669c22bd4b89b198f505126370fez" width="259" /></p >\n\n<p>以前的CKEditor版本由于没',
      mdValue:
        "# markdown测试文档1\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n![网图](https://images.shejidaren.com/wp-content/uploads/2014/07/free-photos.jpg)\n\n# 进阶版编辑器\n## markdown测试文档2\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n#进阶版编辑器\n```javascript\nexport default defineComponent({\n name: 'MdEditor',\n props: {\n value: {\n type: String,\n default: ''\n }\n },\n setup(props) {\n return () => (\n <MdEditor v-model={[props.value,'modelValue']} />\n );\n }\n});\n```\n\n### markdown测试文档3\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n#进阶版编辑器\n#### markdown测试文档4\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n#进阶版编辑器\n##### markdown测试文档511111111\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n#进阶版编辑器\n###### markdown测试文档6# markdown测试文档1\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n![网图](https://images.shejidaren.com/wp-content/uploads/2014/07/free-photos.jpg)\n\n# 进阶版编辑器\n## markdown测试文档2\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n#进阶版编辑器\n```javascript\nexport default defineComponent({\n name: 'MdEditor',\n props: {\n value: {\n type: String,\n default: ''\n }\n },\n setup(props) {\n return () => (\n <MdEditor v-model={[props.value,'modelValue']} />\n );\n }\n});\n```\n\n## markdown测试文档3\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n#进阶版编辑器\n## markdown测试文档4\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n#进阶版编辑器\n## markdown测试文档5\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n#进阶版编辑器\n## markdown测试文档6",
    };
  },
  mounted() {
    // setTimeout(() => {
    //   this.mdValue =
    //     "# markdown测试文档1\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n$$\nlkasdjsdlkfj\ndsfksdjf\n$$\n\n:grinning:\n[点击跳转](#jump)\n```mermaid\nflowchart TD \n  Start --> Stop\n```\n\n| 表头| 标题|\n| - | - |\n| 闪电发货就| 闪电发货就|\n| 快速的房间| 快乐多发几个|\n\n![](http://image.res.meizu.com/image/open/ce3417fbf98d42428ccfcbcf5428c397z)\n\n![御堂筋](http://image.res.meizu.com/image/open/4fc2dcac91ad4136801d55fe271af8fez)\n\n![网图](https://images.shejidaren.com/wp-content/uploads/2014/07/free-photos.jpg)\n\n#进阶版编辑器\n## markdown测试文档2\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n#进阶版编辑器\n```javascript\nexport default defineComponent({\n  name: 'MdEditor',\n  props: {\n    value: {\n      type: String,\n      default: ''\n    }\n  },\n  setup(props) {\n    return () => (\n      <MdEditor v-model={[props.value,'modelValue']} />\n    );\n  }\n});\n```\n\n### markdown测试文档3\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n#进阶版编辑器\n![](http://image.res.meizu.com/image/open/f8de36c6a21c4ef8b1dc8ce673746bacz)\n\n#### markdown测试文档4\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n![](http://image.res.meizu.com/image/open/c9077b8f2d0d418ebe7747e68c3ac213z)\n\n#进阶版编辑器\n##### markdown测试文档5\n更为丰富的编辑区功能扩展。例如：无法根据不同的语法在输入框内显示不同的样式。\n![](http://image.res.meizu.com/image/open/a0e819cced36453ba1222b184e9afb53z)\n<span id="jump">跳转到的地方</span>\n#进阶版编辑器\n###### markdown测试文档6![](undefined)\n```mermaidgraph LR\nA --- B\nB-->C[fa:fa-ban forbidden]\nB-->D(fa:fa-spinner);\n```";
    // }, 1000);
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
