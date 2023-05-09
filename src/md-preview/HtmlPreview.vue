<!--
 * @Author: ZtrainWilliams ztrain1224@163.com
 * @Date: 2023-04-26 19:55:14
 * @Description: md-html-preview html格式的markdown内容预览组件
-->
<template>
  <div class="html-preview">
    <div v-html="htmlContent" ref="preview" class="html-preview-content"></div>
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
import "./assets/default.css";
import "./assets/atom-one-dark.min.css";
import hljs from "./assets/highlight.min.js";

export default {
  name: "html-preview",
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
      htmlContent: "",
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
        this.htmlContent = v;
        this.setLinks();
      },
      immediate: true,
    },
  },
  created() {},
  methods: {
    setLinks() {
      this.$nextTick(() => {
        hljs && hljs.initHighlightingOnLoad();
      });
      if (!this.showLinks) return;
      this.$nextTick(() => {
        const anchors = this.$refs.preview
          ? this.$refs.preview.querySelectorAll("h1,h2,h3,h4,h5,h6")
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

        this.links = titles.map((el, i) => {
          el.setAttribute("data-v-md-line", i); // 设置锚点标记
          return {
            title: el.innerText,
            lineIndex: i,
            indent: hTags.indexOf(el.tagName),
          };
        });
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
      const heading = this.$refs.preview.querySelector(
        `[data-v-md-line="${item.lineIndex}"]`
      );

      if (heading) {
        heading.scrollIntoView({ block: "start", behavior: "smooth" });
      }
    },
  },
};
</script>
<style lang="css">
.html-preview {
  display: flex;
  position: relative;
  padding-right: 240px;
}
.html-preview-content {
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
