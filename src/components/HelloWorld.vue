<template>
  <div class="hello">
    <input type="text" v-model="user">
    <input type="text" v-model="plusOne">
    <div>{{plusOne}}</div>
    <button @click="btn">登录</button>
  </div>
</template>

<script>
import { toRefs, reactive, computed, ref, onActivated, onBeforeMount, onBeforeUnmount, onBeforeUpdate, onDeactivated, onMounted, onUnmounted, onUpdated } from '@vue/composition-api'
export default {
  name: 'HelloWorld',
  setup (props, {root}) {
    const state = reactive({
      user: '',
      password: ''
    })
    const count = ref(1)
    const plusOne = computed({
      get: () => {
        count.value + 1
      },
      set: val => { count.value = val - 1 }
    })
    onActivated(() => {
      console.log('onActivated')
    })
    onBeforeMount(() => console.log('onBeforeMount'))
    onBeforeUnmount(() => console.log('onBeforeUnmount'))
    onBeforeUpdate(() => console.log('onBeforeUpdate'))
    onDeactivated(() => console.log('onDeactivated'))
    onMounted(() => console.log('onMounted'))
    onUnmounted(() => console.log('onUnmounted'))
    onUpdated((a) => {
      console.log('onUpdated', a)
    })
    const btn = () => {
      let {user, password} = state
      console.log(user, password, root)
    }
    return {
      ...toRefs(state),
      btn,
      plusOne
    }
  }
}
</script>

<style scoped>
</style>
