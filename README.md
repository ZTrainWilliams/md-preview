## markdown 预览组件 - md-preview

基于@kangc/v-md-editor 、vue2 的 markdown 预览组件，封装包含功能代码高亮、katex 公式、流程图、Emoji、代码复制、代码行、todoList、提示
组件右侧可开启树形大纲，支持收起跳转。

<img src="https://github.com/ZTrainWilliams/md-preview/blob/main/asset/view.jpg" alt="view">

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
