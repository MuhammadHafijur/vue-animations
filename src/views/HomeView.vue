<template>
  <div class="home">
    <TheToast v-if="showToast" />
    <TheTodos @badValue="triggerToast" />
    <Transition name="fade">
      <div v-if="showP">Hello, people!</div>
    </Transition>

    <button @click="showP = !showP">toggle</button>
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
    const showP = ref(false)

    const triggerToast = () => {
      showToast.value = true;
      setTimeout(() => showToast.value = false, 3000)
    }

    return { showToast, triggerToast, showP }
  }
}
</script>

<style>
.fade-enter-from{
  opacity: 0;

}
.fade-enter-to{
  opacity: 1;
}
.fade-enter-active{
  transition: all 2s ease;
}
.fade-leave-from{
  opacity: 1;
}
.fade-leave-to{
  opacity: 0;
}
.fade-leave-active{
  transition: all 2s ease;
}


</style>