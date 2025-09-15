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
      <button class="button is-success" @click="saveArticle">SAVE</button>
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
  methods: {
    //create new Article
    async saveArticle() {
      try {
        await axios.post('http://localhost:5000/articles', {
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
