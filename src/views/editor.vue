<script setup lang="ts" name="editor">
import WangEditor from 'wangeditor'
import { onBeforeUnmount, onMounted, reactive, ref } from 'vue'

const editor = ref(null)
const content = reactive({
  html: '',
  text: '',
})
let instance: any
onMounted(() => {
  instance = new WangEditor(editor.value)
  instance.config.zIndex = 1
  instance.create()
})
onBeforeUnmount(() => {
  instance.destroy()
  instance = null
})
const syncHTML = () => {
  content.html = instance.txt.html()
  console.log(content.html)
}
</script>

<template>
  <div class="container">
    <div class="plugins-tips">
      wangEditor：轻量级 web 富文本编辑器，配置方便，使用简单。 访问地址：
      <a href="https://www.wangeditor.com/doc/" target="_blank">wangEditor</a>
    </div>
    <div ref="editor" class="mgb20" />
    <el-button type="primary" @click="syncHTML">
      提交
    </el-button>
  </div>
</template>

<style></style>
