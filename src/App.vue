<template>
  <div class="container column">
    <ResumeForm @block-added="addBlock"/>
    <ResumeView :blocks="blocks"/>

  </div>
  <div class="container">
    <AppLoader v-if="loading"/>
    <ResumeComments
      v-else
      @load-comments="loadComments"
      :comments="comments"
    />
  </div>
</template>

<script>
import ResumeForm from './components/ResumeForm.vue'
import ResumeView from './components/ResumeView.vue'
import ResumeComments from './components/ResumeComments.vue'
import AppLoader from './components/AppLoader.vue'

export default {
  data () {
    return {
      blocks: [],
      comments: [],
      loading: false
    }
  },
  methods: {
    addBlock (block) {
      this.blocks.push(block)
    },
    async loadComments () {
      this.loading = true
      const res = await fetch('https://jsonplaceholder.typicode.com/comments?_limit=42')
      this.comments = await res.json()
      this.loading = false
    }
  },
  components: { ResumeForm, ResumeView, ResumeComments, AppLoader }
}
</script>

<style>

</style>
