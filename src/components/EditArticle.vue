<template>
  <div>
    <div class="field">
      <label class="label">Title</label>
      <div class="control">
        <input class="input" type="text" placeholder="Title" v-model="ArticleTitle" />
      </div>
    </div>

    <div class="field">
      <label class="label">Body</label>
      <div class="control">
        <input class="input" type="text" placeholder="Body" v-model="ArticleBody" />
      </div>
    </div>

    <div class="control">
      <button class="button is-success" @click="updateArticle">UPDATE</button>
    </div>
  </div>
</template>

<script>
//import axios
import axios from 'axios'

export default {
  data() {
    return {
      ArticleTitle: '',
      ArticleBody: '',
    }
  },
  created: function () {
    this.getArticleById()
  },
  methods: {
    //get product by id
    async getArticleById() {
      try {
        const response = await axios.get(`http://localhost:5000/articles/${this.$route.params.id}`)
        this.ArticleTitle = response.data.title
        this.ArticleBody = response.data.body
      } catch (err) {
        console.log(err)
      }
    },

    //update product
    async updateArticle() {
      try {
        await axios.put(`http://localhost:5000/articles/${this.$route.params.id}`, {
          title: this.ArticleTitle,
          body: this.ArticleBody,
        })
        ;((this.ArticleTitle = ''), (this.ArticleBody = ''))
        this.$router.push('/')
      } catch (err) {
        console.log(err)
      }
    },
  },
}
</script>

<style></style>
