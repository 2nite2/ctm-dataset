<template>
  <div class="p-3 mb-4 mx-auto lg:w-6/12 bg-gray-200 rounded-lg shadow-xl">
    <h2 class="mb-3 mr-3 text-2xl text-center font-bold text-gray-600">
      Search Book
    </h2>

    <div
      :class="showInput === false ? 'hidden' : 'block'"
      class="flex flex-row items-center justify-between"
    >
      <input
        v-model="query"
        type="text"
        class="
          p-2
          m-2
          w-full
          rounded-lg
          border-0
          shadow-md
          focus:ring-2 focus:ring-blue-500
          text-lg
        "
        placeholder="Book Title"
        @keyup.enter="addSearch"
      />
      <button
        class="
          p-2
          w-11
          h-11
          flex
          justify-center
          items-center
          rounded-full
          text-white text-lg
          font-bold
          bg-gradient-to-r
          from-indigo-400
          to-blue-500
          hover:from-indigo-500 hover:to-blue-600 hover:bg-blue-600
          hidden
          md:flex
        "
        @click="addSearch"
      >
        <i class="fas fa-search"></i>
      </button>
    </div>

    <div class="p-2 flex justify-center">
      <i
        class="fas fa-chevron-down fa-lg cursor-pointer"
        @click="toggleShowInput"
      ></i>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'
import { useStore } from 'vuex'

export default {
  name: 'Search',
  setup() {
    const store = useStore()

    const query = ref('')

    const showInput = ref(false)

    const addSearch = async () => {
      if (query.value !== '') {
        await store.dispatch('addSearch', {
          query: query.value,
          status: true,
        })
        return (query.value = '')
      }
      return await store.dispatch('addSearch', {
        query: '',
        status: false,
      })
    }

    const toggleShowInput = () =>
      showInput.value === false
        ? (showInput.value = true)
        : (showInput.value = false)

    return {
      showInput,
      query,
      addSearch,
      toggleShowInput,
    }
  },
}
</script>
