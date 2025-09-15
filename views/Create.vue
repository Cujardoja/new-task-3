<template>
  <div>
    <AddArticle />
  </div>
</template>

<script>
// @ is an alias to /src
import AddArticle from '@/components/AddArticle.vue'
export default {
  name: 'Create',
  components: {
    AddArticle,
  },
}
</script>
