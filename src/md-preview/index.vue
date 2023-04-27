<!--
 * @Author: ZtrainWilliams ztrain1224@163.com
 * @Date: 2023-04-26 19:55:14
 * @Description: md-preview markdown 预览组件
-->
<template>
  <div class="md-preview">
    <v-md-preview :text="docDetail" ref="preview"></v-md-preview>
    <div v-if="showLinks" class="preview-links">
      <el-tree
        :data="data"
        :props="defaultProps"
        default-expand-all
        :expand-on-click-node="false"
        @node-click="handleClick"
      >
        <span slot-scope="{ node }">
          <span class="custom-tree-node-label" :title="node.label">
            {{ node.label }}
          </span>
        </span>
      </el-tree>
    </div>
  </div>
</template>
<script>
import Vue from "vue";
import VMdPreview from "@kangc/v-md-editor/lib/preview";
import "@kangc/v-md-editor/lib/style/preview.css";
import vuepressTheme from "@kangc/v-md-editor/lib/theme/vuepress.js";
import "@kangc/v-md-editor/lib/theme/style/vuepress.css";
import Prism from "prismjs";
import katex from "katex/dist/katex.min.js";
import "katex/dist/katex.css";
import createKatexPlugin from "@kangc/v-md-editor/lib/plugins/katex/npm";
import mermaid from 'mermaid/dist/mermaid.js'
import createMermaidPlugin from "@kangc/v-md-editor/lib/plugins/mermaid/npm";
import "@kangc/v-md-editor/lib/plugins/mermaid/mermaid.css";
import createCopyCodePlugin from "@kangc/v-md-editor/lib/plugins/copy-code/index";
import "@kangc/v-md-editor/lib/plugins/copy-code/copy-code.css";
import createEmojiPlugin from "@kangc/v-md-editor/lib/plugins/emoji/index";
import "@kangc/v-md-editor/lib/plugins/emoji/emoji.css";
import createTodoListPlugin from "@kangc/v-md-editor/lib/plugins/todo-list/index";
import "@kangc/v-md-editor/lib/plugins/todo-list/todo-list.css";
import createLineNumbertPlugin from "@kangc/v-md-editor/lib/plugins/line-number/index";
import createTipPlugin from "@kangc/v-md-editor/lib/plugins/tip/index";
import "@kangc/v-md-editor/lib/plugins/tip/tip.css";

VMdPreview.use(vuepressTheme, {
  Prism,
});
VMdPreview.use(createKatexPlugin(katex)); // katex 公式
VMdPreview.use(createMermaidPlugin(mermaid)); // 流程图
VMdPreview.use(createEmojiPlugin()); // Emoji
VMdPreview.use(createCopyCodePlugin()); // 代码复制
VMdPreview.use(createLineNumbertPlugin()); // 代码行号
VMdPreview.use(createTodoListPlugin()); // TODO List
VMdPreview.use(createTipPlugin()); // 提示
Vue.use(VMdPreview);

export default {
  name: "md-preview",
  props: {
    value: {
      type: String,
    },
    showLinks: {
      type: Boolean,
      default: true,
    },
  },
  data() {
    return {
      docDetail: "",
      links: [],
      data: [],
      defaultProps: {
        children: "children",
        label: "title",
      },
    };
  },
  watch: {
    value: {
      handler(v) {
        this.docDetail = v;
        this.setLinks();
      },
      immediate: true,
    },
  },
  created() {},
  methods: {
    setLinks() {
      if (!this.showLinks) return;
      this.$nextTick(() => {
        const anchors = this.$refs.preview
          ? this.$refs.preview.$el.querySelectorAll("h1,h2,h3,h4,h5,h6")
          : [];
        const titles = Array.from(anchors).filter(
          (title) => !!title.innerText.trim()
        );

        if (!titles.length) {
          this.links = [];
          this.setTreeData(this.links);
          return;
        }

        const hTags = Array.from(
          new Set(titles.map((title) => title.tagName))
        ).sort();

        this.links = titles.map((el) => ({
          title: el.innerText,
          lineIndex: el.getAttribute("data-v-md-line"),
          indent: hTags.indexOf(el.tagName),
        }));
        this.setTreeData(this.links);
      });
    },
    setTreeData(list) {
      const tocItems = [];

      list.forEach((row, index) => {
        const { title, indent } = row;
        const item = { indent, title, index: index + 1, ...row };

        if (tocItems.length === 0) {
          // 第一个 item 直接 push
          tocItems.push(item);
        } else {
          let lastItem = tocItems[tocItems.length - 1]; // 最后一个 item

          if (item.indent > lastItem.indent) {
            // item 是 lastItem 的 children
            for (let i = lastItem.indent + 1; i <= 6; i++) {
              const { children } = lastItem;
              if (!children) {
                // 如果 children 不存在
                lastItem.children = [item];
                break;
              }

              lastItem = children[children.length - 1]; // 重置 lastItem 为 children 的最后一个 item

              if (item.indent <= lastItem.indent) {
                // item indent 小于或等于 lastItem indent 都视为与 children 同级
                children.push(item);
                break;
              }
            }
          } else {
            // 置于最顶级
            tocItems.push(item);
          }
        }
      });
      this.data = tocItems;
    },
    handleClick(item) {
      const heading = this.$refs.preview.$el.querySelector(
        `[data-v-md-line="${item.lineIndex}"]`
      );

      if (heading) {
        this.$refs.preview.scrollToTarget({
          target: heading,
          scrollContainer: window,
          top: 60,
        });
      }
    },
  },
};
</script>
<style lang="css">
.md-preview {
  display: flex;
  position: relative;
  padding-right: 240px;
}
.v-md-editor-preview {
  flex: 1;
}
.preview-links {
  width: 240px;
  position: fixed;
  z-index: 998;
  right: 0;
  top: 52px;
  max-width: 305px;
  height: calc(100vh - 52px);
  max-height: calc(100vh - 52px);
  overflow-y: auto;
  overflow-x: hidden;
}
.preview-links .el-tree {
  background-color: #fafafa;
}
.el-tree-node__content {
  padding: 2px 0;
  font-size: 14px;
  height: auto;
  min-height: 24px;
}
.custom-tree-node-label {
  white-space: normal;
}
</style>
