<template>
  <div>
    <VueEditor v-model="content" ref="myQuillEditor" :editorToolbar="customToolbar"
      :editorOptions="editorSettings" @text-change="onEditorChange">
    </VueEditor>
  </div>
</template>

<script>
import { VueEditor, Quill } from 'vue2-editor'
import { ImageDrop } from 'quill-image-drop-module'
import QuillResize from 'quill-resize-module'
import defaultToolbar from './defaultToolBar'

Quill.register('modules/imageDrop', ImageDrop)
Quill.register('modules/resize', QuillResize)
export default {
  props: ['value'],
  components: {
    VueEditor
  },
  data () {
    return {
      content: '',
      customToolbar: defaultToolbar,
      editorSettings: {
        modules: {
          imageDrop: true,
          resize: {
            modules: ['Resize', 'DisplaySize', 'Toolbar']
          }
        }
      }
    }
  },
  methods: {
    onEditorChange () {
      this.$emit('input', this.content)
    }
  }
}
</script>

<style scoped>
  ::v-deep .ql-container {
    overflow: hidden;
  }
  ::v-deep .ql-editor {
    min-height: 260px;
    max-height: 450px;
  }
</style>
