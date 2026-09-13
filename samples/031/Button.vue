<template>
  <button :class="btnClass" @click="customClick"></button>
</template>

<script>
import { reactive, toRefs } from 'vue'

export default {
  name: 'Button',
  props: {
    buttonClass: {
      type: String,
      required: true,
    },
  },
  emits: ['click-event'],
  setup(props, { emit }) {
    const btn = reactive({
      btnClass: props.buttonClass,
    })

    const customClick = async (event) =>
      await emit('click-event', event.target.value)

    return {
      ...toRefs(btn),
      customClick,
    }
  },
}
</script>
