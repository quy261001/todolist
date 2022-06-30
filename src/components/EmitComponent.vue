<template>
   <div> {{ testEmit }} </div>
   <input type="text" placeholder="Custom Text Input" @change="onChangeEmit" />
</template>

<script>
  import { toRefs } from 'vue'
export default {
  props: ['testEmit'],
  setup(props, { emit }) {
    const {testEmit} = toRefs(props)
    console.log(testEmit.value);

     function onChangeEmit(e) {
      emit(
        'customChange',
        e.target.value
      )
     }
    return {onChangeEmit}
  }
}
</script>