<script>
import Modal from './Modal.vue'
import DiffMatchPatch from 'diff-match-patch'

const dmp = new DiffMatchPatch()

export default {
  components: {
    Modal
  },
  methods: {
    launch() {
      var text1 = document.getElementById('text1').value
      var text2 = document.getElementById('text2').value
      var d = dmp.diff_main(text1, text2)
      dmp.diff_cleanupSemantic(d)
      var ds = dmp.diff_prettyHtml(d)
      this.diff = ds
      this.showModal = true
    }
  },
  data() {
    return {
      showModal: false,
      diff: ""
    }
  }
}
</script>

<template>
  <h3>text1</h3>
  <textarea id="text1" style="width: 100%" row=10>I am the very model of a modern Major-General,
I've information vegetable, animal, and mineral,
I know the kings of England, and I quote the fights historical,
From Marathon to Waterloo, in order categorical.</textarea>
  <h3>text2</h3>
  <textarea id="text2" style="width: 100%" row=10>I am the very model of a cartoon individual,
My animation's comical, unusual, and whimsical,
I'm quite adept at funny gags, comedic theory I have read,
From wicked puns and stupid jokes to anvils that drop on your head.</textarea>
  <button id="show-modal" @click="launch()">Show Modal</button>

  <Teleport to="body">
    <modal :show="showModal" @close="showModal = false">
      <template #header>
        <h3>Diff</h3>
      </template>
      <template #body>
        <div v-html="diff"></div>
      </template>
    </modal>
  </Teleport>
</template>
