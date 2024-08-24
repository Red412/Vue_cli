<template>
  <div class="card card-w70">
    <template v-if="blocks.length">
      <component
        v-for="block in blocks"
        :key="block.id"
        :is="'resume-' + block.type"
        v-bind="{value: block.value}"
      ></component>
    </template>
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
import ResumeTitle from './parts/ResumeTitle.vue'
import ResumeSubtitle from './parts/ResumeSubtitle.vue'
import ResumeText from './parts/ResumeText.vue'
import ResumeAvatar from './parts/ResumeAvatar.vue'

export default {
  props: ['blocks'],
  components: { ResumeTitle, ResumeSubtitle, ResumeText, ResumeAvatar }
}
</script>
