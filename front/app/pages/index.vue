<template>
  <div class="container">
    <div>
      <editor-content :editor="editor" />
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

// Import the editor
import { Editor, EditorContent } from 'tiptap'

export default Vue.extend({
  components: {
    EditorContent,
  },
  data() {
    return {
      editor: null as Editor | null,
    }
  },
  mounted() {
    this.editor = new Editor({
      content: '<p>テキストを編集できますよ</p>',
    })
  },
  beforeDestroy() {
    this.editor?.destroy()
  },
});
</script>


</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

</style>
