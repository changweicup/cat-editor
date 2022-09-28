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
import 'vue2-editor/dist/vue2-editor.css'

/* Import the Quill styles you want */
import 'quill/dist/quill.core.css'
import 'quill/dist/quill.bubble.css'
import 'quill/dist/quill.snow.css'

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
            modules: ['Resize', 'DisplaySize']
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
