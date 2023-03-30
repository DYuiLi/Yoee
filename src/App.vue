<template>
  <div id="root">
    <h1>APP组件</h1>
    <Suspense>
      <template v-slot:default>
        <Child></Child>
      </template>
      <template v-slot:fallback>
        <h2>Loading...</h2>
      </template>
    </Suspense>
  </div>
</template>

<script>
import { defineAsyncComponent } from 'vue'
const Child = defineAsyncComponent(() =>import('./components/Child.vue'))
import { reactive, provide, toRefs } from 'vue'
// import Child from './components/Child.vue'

export default {
  name: 'App',
  components: {Child},

  setup(){
    const person = reactive({
      name: 'Yui',
      age: 24,
    })
    
    return { ...toRefs(person)}
  }
}
</script>

<style>
  #root {
    height: 500px;
    background-color: skyblue;
  }
</style>
