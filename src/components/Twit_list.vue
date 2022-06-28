<template>
  <select v-model="sortBy">
    <option value="date">Sort by date</option>
    <option value="likes">Sort by like</option>
  </select>
  <ul class="tweets__wrapper">
    <Twit_content v-for="item in sorteredItems" :key="item.id" :item="item" />
  </ul>
</template>

<script>
import { ref, computed } from 'vue'
import Twit_content from '@/components/Twit_content.vue'
export default {
  components: { Twit_content },
  props: {
    items: {
      type: Array,
      reqired: true
    }
  },
  setup({ items }) {
    const sortBy = ref('date')
    const sorteredItems = computed(() => {
      return items.sort((a, b) => {
        if (a[sortBy.value] > b[sortBy.value]) return -1
        if (a[sortBy.value] < b[sortBy.value]) return 1
      })
    })
    return { sortBy, sorteredItems }
  }
}
</script>