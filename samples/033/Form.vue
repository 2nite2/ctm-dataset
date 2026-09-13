<template>
  <div class="p-4 mb-5 mx-auto lg:w-6/12 bg-gray-200 rounded-lg shadow-xl">
    <h2 class="mb-2 text-2xl text-center font-bold text-gray-600">
      Add New Book
    </h2>
    <form
      :class="showInput === false ? 'hidden' : 'block'"
      class="mb-2"
      @submit.prevent="addBook"
    >
      <div class="mb-3">
        <label for="bookTitle" class="text-xl font-bold text-gray-600"
          >Title</label
        >
        <br />
        <input
          id="bookTitle"
          v-model="bookTitle"
          type="text"
          class="
            p-2
            mt-2
            rounded-lg
            w-full
            border-0
            shadow-md
            focus:ring-2 focus:ring-blue-500
            text-lg
          "
          placeholder="Book Title"
          required
        />
      </div>

      <div class="mb-3">
        <label for="bookAuthor" class="text-xl font-bold text-gray-600"
          >Author</label
        >
        <br />
        <input
          id="bookAuthor"
          v-model="bookAuthor"
          type="text"
          class="
            p-2
            mt-2
            rounded-lg
            w-full
            border-0
            shadow-md
            focus:ring-2 focus:ring-blue-500
            text-lg
          "
          placeholder="Book Author"
          required
        />
      </div>

      <div class="mb-3">
        <label for="bookYear" class="text-xl font-bold text-gray-600"
          >Year</label
        >
        <br />
        <input
          id="bookYear"
          v-model="bookYear"
          type="text"
          class="
            p-2
            mt-2
            rounded-lg
            w-full
            border-0
            shadow-md
            focus:ring-2 focus:ring-blue-500
            text-lg
          "
          placeholder="Book Year"
          required
        />
      </div>

      <div class="mb-3 flex items-center">
        <label
          for="bookisComplete"
          class="flex-initial text-xl font-bold text-gray-600"
          >Completed</label
        >
        <input
          id="bookisComplete"
          v-model="bookisComplete"
          type="checkbox"
          class="
            flex-none
            p-2
            ml-2
            rounded-sm
            border-0
            shadow-md
            focus:ring-2 focus:ring-blue-500
            text-lg
          "
        />
      </div>

      <button
        type="submit"
        class="
          p-2
          w-full
          rounded-lg
          text-white text-lg
          font-bold
          bg-gradient-to-r
          from-indigo-400
          to-blue-500
          hover:from-indigo-500 hover:to-blue-600 hover:bg-blue-600
        "
      >
        Add Book
      </button>
    </form>

    <div class="p-2 flex justify-center">
      <i
        class="fas fa-chevron-down fa-lg cursor-pointer"
        @click="toggleShowInput"
      ></i>
    </div>
  </div>
</template>

<script>
import { ref, reactive, toRefs } from 'vue'
import { useStore } from 'vuex'

export default {
  name: 'Form',
  setup() {
    const store = useStore()

    const showInput = ref(false)

    const toggleShowInput = () =>
      showInput.value === false
        ? (showInput.value = true)
        : (showInput.value = false)

    const initialState = {
      bookTitle: '',
      bookAuthor: '',
      bookYear: null,
      bookisComplete: false,
    }

    const formState = reactive(initialState)

    const addBook = async () => {
      if (formState !== initialState) {
        await store.dispatch('addBook', formState)
        return clearForm()
      }
      return null
    }

    const clearForm = () => {
      formState.bookTitle = ''
      formState.bookAuthor = ''
      formState.bookYear = null
      formState.bookisComplete = false
      return formState
    }

    return {
      ...toRefs(formState),
      showInput,
      toggleShowInput,
      addBook,
    }
  },
}
</script>
