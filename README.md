## markdown 预览组件 - md-preview

基于@kangc/v-md-editor 、vue2 的 markdown 预览组件，封装包含功能代码高亮、katex 公式、流程图、Emoji、代码复制、代码行、todoList、提示
组件右侧可开启树形大纲，支持收起跳转。

<img src="https://github.com/ZTrainWilliams/md-preview/asset/view.jpg" alt="view">

### 依赖

- 公式需要依赖：katex
- 流程图需要依赖： mermaid@9.4.0

### 其他

[v-md-editor](http://ckang1229.gitee.io/vue-markdown-editor/zh/)
公式、流程图实现官方文档都有 demo，demo 是以 cdn 形式引入，可对应更改。

mermaid 的 demo-cdn 链接不可用，需要指定版本

```javascript
<script src="https://unpkg.com/mermaid@9.4.0/dist/mermaid.min.js"></script>
```

mermaid@9.4.0支持 ssr

增加markdown转成html格式的预览组件，HtmlPreview。


#### vue@3

vue3可使用 [md-editor-v3](https://imzbf.github.io/md-editor-v3/zh-CN/demo#%F0%9F%93%84%20%E7%9B%AE%E5%BD%95%E8%8E%B7%E5%8F%96%E4%B8%8E%E5%B1%95%E7%A4%BA)
