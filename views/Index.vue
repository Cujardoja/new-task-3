<template>
  <div>
    <ArticleList />
  </div>
</template>

<script>
// @ is an alias to /src
import ArticleList from '@/components/ArticleList.vue'

export default {
  name: 'Index',
  components: {
    ArticleList,
  },
}
</script>
