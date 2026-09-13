<template>
  <div class="p-3 mb-4 mx-auto lg:w-6/12 bg-gray-200 rounded-lg shadow-xl">
    <h2 class="mb-4 text-2xl font-bold text-gray-600">Not Finished Reading</h2>
    <div
      v-for="inCompleteBook in inCompleteBooks"
      :key="inCompleteBook.id"
      :class="
        getSearchStatus === true && inCompleteBook.title !== findBookTitle
          ? 'hidden'
          : 'block'
      "
      class="
        p-3
        mb-2
        mx-auto
        w-full
        bg-gradient-to-r
        from-indigo-400
        to-blue-500
        rounded-lg
        shadow-xl
        text-white text-lg
      "
    >
      <p class="text-xl font-bold">{{ inCompleteBook.title }}</p>
      <p>Author: {{ inCompleteBook.author }}</p>
      <p>Year: {{ inCompleteBook.year }}</p>

      <div class="mt-3 w-full flex flex-row">
        <Button
          button-title="Remove"
          button-class="
        p-2
        m-2
        w-1/2
        md:w-14
        md:h-14
        md:flex
        md:justify-center
        md:items-center
        md:rounded-full
        text-lg
        rounded-lg
        bg-red-500
        hover:bg-red-600
        far fa-trash-alt fa-7x
        "
          @click-event="removeBook(inCompleteBook.id)"
        />

        <Button
          button-title="Not Finished"
          button-class="
            p-2
            m-2
            w-1/2
            md:w-14
        md:h-14
        md:flex
        md:justify-center
        md:items-center
        md:rounded-full
            text-lg
            rounded-lg
            bg-green-500
            hover:bg-green-600
            fas fa-check fa-7x
            "
          @click-event="addBookToComplete(inCompleteBook.id)"
        />
      </div>
    </div>
  </div>

  <div class="p-3 mb-4 mx-auto lg:w-6/12 bg-gray-200 rounded-lg shadow-xl">
    <h2 class="mb-4 text-2xl font-bold text-gray-600">Finished Reading</h2>
    <div
      v-for="completeBook in completeBooks"
      :key="completeBook.id"
      :class="
        getSearchStatus === true && completeBook.title !== findBookTitle
          ? 'hidden'
          : 'block'
      "
      class="
        p-3
        mb-2
        mx-auto
        w-full
        bg-gradient-to-r
        from-indigo-400
        to-blue-500
        rounded-lg
        shadow-xl
        text-white text-lg
      "
    >
      <p class="text-xl font-bold">{{ completeBook.title }}</p>
      <p>Author: {{ completeBook.author }}</p>
      <p>Year: {{ completeBook.year }}</p>

      <div class="mt-3 w-full flex flex-row">
        <Button
          button-title="Remove"
          button-class="
        p-2
        m-2
        w-1/2
        md:w-14
        md:h-14
        md:flex
        md:justify-center
        md:items-center
        md:rounded-full
        text-lg
        rounded-lg
        bg-red-500
        hover:bg-red-600
        far fa-trash-alt fa-7x
        "
          @click-event="removeBook(completeBook.id)"
        />

        <Button
          button-title="Not Finished"
          button-class="
        p-2
        m-2
        w-1/2
        md:w-14
        md:h-14
        md:flex
        md:justify-center
        md:items-center
        md:rounded-full
        text-lg
        rounded-lg
        bg-yellow-500
        hover:bg-yellow-600
        fas fa-times fa-7x
        "
          @click-event="addBookToInComplete(completeBook.id)"
        />
      </div>
    </div>
  </div>
</template>

<script>
import { computed } from 'vue'
import { useStore } from 'vuex'

import Button from './Button.vue'

export default {
  name: 'Bookshelf',
  components: {
    Button,
  },
  setup() {
    const store = useStore()

    const removeBook = (id) =>
      store.dispatch('removeBook', store.getters.findBookIndex(id))

    const addBookToComplete = (id) =>
      store.dispatch('addBookToComplete', store.getters.findBookIndex(id))

    const addBookToInComplete = (id) =>
      store.dispatch('addBookToInComplete', store.getters.findBookIndex(id))

    return {
      inCompleteBooks: computed(() => store.getters.inCompleteBooks),
      completeBooks: computed(() => store.getters.completeBooks),
      getSearchStatus: computed(() => store.getters.getSearchStatus),
      findBookTitle: computed(() => store.getters.findBookTitle),
      removeBook,
      addBookToComplete,
      addBookToInComplete,
    }
  },
}
</script>
