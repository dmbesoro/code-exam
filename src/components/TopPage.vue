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
    };
  },
  async created() {
    const { data } = await axios.get("http://localhost:3000/articles").then(res => {this.articles = res.data});
  },
  methods: {
    async deleteArticle(id){
      const { data } = await axios.delete(`http://localhost:3000/articles/${id}`);
      this.$forceUpdate();

    }
  }
};
</script>

<template>
  <div>
    <h1>Simple Bulletin Board</h1>
    <router-link to="/create">Create New Article</router-link>
    <ul id="example-1">
      <li v-for="article in articles" :key="article.id">
        <router-link to="/create">{{ article.article_title }}</router-link>
        <h4>{{ article.article_text }}</h4>
        <router-link to="/create">Edit Article</router-link>
        <button @click="deleteArticle(article.id)">delete</button>
      </li>
    </ul>
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