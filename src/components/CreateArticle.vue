<script>
import axios from 'axios';
export default {
  props: {
    title: String,
  },
  setup(props) {
    console.log(props.title);
  },
  data() {
    return {
      articles: [],
      title: "",
      text: "",
    };
  },
  methods: {
    async postArticle() {
      const { data } = await axios.post("http://localhost:3000/articles", {
        article_title: this.title,
        article_text: this.text,
      });
      this.$router.push('/');
    },
  },
};
</script>

<template>
  <div>
    <h1>Create Article</h1>
    <label for="title">Title:</label>
    <input v-model="title" type="text" id="title" name="title" /><br /><br />
    <label for="text">Text:</label>
    <input v-model="text" type="text" id="text" name="text" /><br /><br />
    <button @click="postArticle()">Save</button>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>