<script>
export default {
  props: {
    title: String,
  },
  setup(props) {
    console.log(props.title);
  },
  data() {
    return {
      articles: [
        {
          id: 1,
          article_title: "Article 1",
          article_text: "Article 1 text",
        },
        {
          id: 2,
          article_title: "Article 2",
          article_text: "Article 2 text",
        },
        {
          id: 1,
          article_title: "Article 2",
          article_text: "Article 2 text",
        },
      ],
    };
  },
};
</script>

<template>
  <div>
    <h1>Article Detail</h1>
    <ul id="example-1">
      <li v-for="article in articles" :key="article.id">
        <h3>{{ article.article_title }}</h3>
        <h4>{{ article.article_text }}</h4>
        
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