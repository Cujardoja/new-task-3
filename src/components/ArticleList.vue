<template>
  <div>
    <router-link :to="{ name: 'Create' }" class="button is-success mt-5"
      >Add New Article</router-link
    >
    <table class="table is-striped is-bordered mt-2 is-fullwidth">
      <thead>
        <tr>
          <!-- <th>ID</th> -->
          <th>Title</th>
          <th>Body</th>
          <th class="has-text-centered">Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in items" v-bind:key="item.id">
          <td>
            {{ item.title }}
          </td>
          <td>{{ item.body }}</td>
          <td class="has-text-centered">
            <router-link
              :to="{ name: 'Edit', params: { id: item.id } }"
              class="button is-info is-small"
              >Edit</router-link
            >
            <a class="button is-danger is-small" @click="deleteArticle(item.id)">Delete</a>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
//import axios
import axios from 'axios'

export default {
  data() {
    return {
      items: [],
    }
  },
  created() {
    this.getArticles()
  },
  methods: {
    //get all products
    async getArticles() {
      try {
        const response = await axios.get('http://localhost:5000/articles')
        this.items = response.data
        console.log(this.items)
      } catch (err) {
        console.log(err)
      }
    },
    //delete product
    async deleteArticle(id) {
      try {
        await axios.delete(`http://localhost:5000/articles/${id}`)
        this.getArticles()
      } catch (err) {
        console.log(err)
      }
    },
  },
}
</script>

<style></style>
