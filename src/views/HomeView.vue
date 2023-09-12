<template>
  <div class="home">
    <TheToast v-if="showToast" />
    <TheTodos @badValue="triggerToast" />
  </div>
</template>

<script>
import { ref } from 'vue'
import TheToast from '../components/TheToast.vue'
import TheTodos from '../components/TheTodos.vue'

export default {
  components: { TheToast, TheTodos },
  setup() {
    const showToast = ref(false)

    const triggerToast = () => {
      showToast.value = true;
      setTimeout(() => showToast.value = false, 3000)
    }

    return { showToast, triggerToast }
  }
}
</script>

<style>

</style>