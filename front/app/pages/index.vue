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
import {
  Blockquote,
  CodeBlock,
  HardBreak,
  Heading,
  HorizontalRule,
  OrderedList,
  BulletList,
  ListItem,
  TodoItem,
  TodoList,
  Bold,
  Code,
  Italic,
  Link,
  Strike,
  Underline,
  History,
} from 'tiptap-extensions'

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
      extensions: [
        new Blockquote(),
        new BulletList(),
        new CodeBlock(),
        new HardBreak(),
        new Heading({ levels: [1, 2, 3] }),
        new HorizontalRule(),
        new ListItem(),
        new OrderedList(),
        new TodoItem(),
        new TodoList(),
        new Link(),
        new Bold(),
        new Code(),
        new Italic(),
        new Strike(),
        new Underline(),
        new History(),
      ],
       content:  `
          <h2>
            Hi there,
          </h2>
          <p>
            this is a very <em>basic</em> example of tiptap.
          </p>
          <pre><code>body { display: none; }</code></pre>
          <ul>
            <li>
              A regular list
            </li>
            <li>
              With regular items
            </li>
          </ul>
          <blockquote>
            It's amazing 👏
            <br />
            – mom
          </blockquote>
        `,
    })
  },
  beforeDestroy() {
    this.editor?.destroy()
  },
});
</script>


<style>
/* Sample `apply` at-rules with Tailwind CSS */
.container {
@apply min-h-screen flex justify-center mx-auto;
}

h1, h2, h3 {
  line-height: 1.3;
  display: block;
  font-size: 1.5em;
  margin-block-start: 0.83em;
  margin-block-end: 0.83em;
  margin-inline-start: 0px;
  margin-inline-end: 0px;
  font-weight: bold;
}

em {
    font-style: italic;
}

pre {
    padding: .7rem 1rem;
    border-radius: 5px;
    background: #000;
    color: #fff;
    font-size: .8rem;
    overflow-x: auto;
}

code {
  font-family: monospace;
}

ol, ul {
  padding-left: 1rem;
}

blockquote, h1, h2, h3, ol, p, pre, ul {
  margin: 1rem 0;
}

ul {
    display: block;
    list-style-type: disc;
    margin-block-start: 1em;
    margin-block-end: 1em;
    margin-inline-start: 0px;
    margin-inline-end: 0px;
    padding-inline-start: 40px;
}
ul {
    list-style-type: disc;
}

blockquote {
    display: block;
    margin-block-start: 1em;
    margin-block-end: 1em;
    margin-inline-start: 40px;
    margin-inline-end: 40px;
}

blockquote {
  border-left: 3px solid rgba(0,0,0,.1);
  color: rgba(0,0,0,.8);
  padding-left: .8rem;
  font-style: italic;
}

.ProseMirror {
  min-width: 50vw;
}

.ProseMirror.ProseMirror-focused {
  outline-color: white;
  outline-width: 0;
}

.li>ol, li>p, li>ul {
    margin: 0;
}

</style>
