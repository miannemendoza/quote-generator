<template>
  <div class="app">
    <Header title="QUOTE GENERATOR" class="header-style" />
    <div class="testDiv" id="gradient">
      <Quote :quote="quote" />
      <button class="no" @click="generateQuote">Generate</button>
    </div>
  </div>
</template>

<script>
import Quote from "./components/Quote.vue";
import Header from "./components/Header.vue";
export default {
  name: "App",
  components: {
    Quote,
    Header,
  },
  data() {
    return {
      quote: {
        content: "",
        author: "",
      },
      quotes: [],
    };
  },
  mounted() {
    let ref = this;
    ref.generateQuote();
  },
  methods: {
    async generateQuote() {
      let ref = this;
      const data = await fetch("https://type.fit/api/quotes").then((res) =>
        res.json()
      );
      const randomNumber = Math.floor(Math.random() * 16) + 1;
      ref.quote = {
        content: data[randomNumber].text,
        author: data[randomNumber].author,
      };
    },
  },
};
</script>

<style lang="scss">
:root {
  --primary: red;
  --secondary: blue;
  --light: white;
  --dark: #2c2f4b;
   background: linear-gradient(126deg, #eebcf3, #7bd6f2, #95e1c3);
    background-size: 600% 600%;

    -webkit-animation: gradient 6s ease infinite;
    -moz-animation: gradient 6s ease infinite;
    animation: gradient 6s ease infinite;
    
@-webkit-keyframes gradient {
    0%{background-position:9% 0%}
    50%{background-position:92% 100%}
    100%{background-position:9% 0%}
}
@-moz-keyframes gradient {
    0%{background-position:9% 0%}
    50%{background-position:92% 100%}
    100%{background-position:9% 0%}
}
@keyframes gradient {
    0%{background-position:9% 0%}
    50%{background-position:92% 100%}
    100%{background-position:9% 0%}
}
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Fira Sans", sans-serif;
}
// .no{
//   float:right;
//   margin-top: -80px;
//   top: calc(100% - 32px);
//   transform: translateY(-50%);
//   margin-right: 12px;
// }
.no {
  margin-bottom: 18px;
 
}
.testDiv {
  background-color: rgb(255, 255, 255);

  box-shadow: 0 2.8px 2.2px rgba(0, 0, 0, 0.034),
    0 6.7px 5.3px rgba(0, 0, 0, 0.048), 0 12.5px 10px rgba(0, 0, 0, 0.06),
    0 22.3px 17.9px rgba(0, 0, 0, 0.072), 0 41.8px 33.4px rgba(0, 0, 0, 0.086),
    0 100px 80px rgba(0, 0, 0, 0.12);
}

button:hover {
  border-color: unset !important;
}

.header-style{
  color: black;
}
</style>
