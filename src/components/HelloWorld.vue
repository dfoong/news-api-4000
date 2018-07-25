<template>
  <div class="hello">
    <form v-on:submit.prevent="getNews">
      <select v-model="country">
        <option value="us">U.S. news</option>
        <option value="gb">UK news</option>
        <option value="ar">Argentina news</option>
        <option value="au">Australia news</option>
        <option value="at">Austria news</option>
        <option value="be">Belgium news</option>
        <option value="br">Brazil news</option>
        <option value="bg">Bulgaria news</option>
        <option value="ca">Canada news</option>
        <option value="cn">China news</option>
        <option value="co">Colombia news</option>
        <option value="cu">Cuba news</option>
        <option value="cz">Czech Republic news</option>
        <option value="eg">Egypt news</option>
        <option value="fr">France news</option>
        <option value="de">Germany news</option>
        <option value="gr">Greece news</option>
        <option value="hk">Hong Kong news</option>
        <option value="hu">Hungary news</option>
        <option value="in">India news</option>
        <option value="id">Indonesia news</option>
        <option value="ie">Ireland news</option>
        <option value="il">Israel news</option>
        <option value="it">Italy news</option>
        <option value="jp">Japan news</option>
        <option value="lv">Latvia news</option>
        <option value="lt">Lithuania news</option>
        <option value="my">Malaysia news</option>
        <option value="mx">Mexico news</option>
        <option value="ma">Morocco news</option>
        <option value="nl">Netherlands news</option>
        <option value="nz">New Zealand news</option>
        <option value="ng">Nigeria news</option>
        <option value="no">Norway news</option>
        <option value="ph">Philippines news</option>
        <option value="pl">Poland news</option>
        <option value="pt">Portugal news</option>
        <option value="ro">Romania news</option>
        <option value="ru">Russia news</option>
        <option value="sa">Saudi Arabia news</option>
        <option value="rs">Serbia news</option>
        <option value="sg">Singapore news</option>
        <option value="si">Slovakia news</option>
        <option value="si">Slovenia news</option>
        <option value="za">South Africa news</option>
        <option value="kr">South Korea news</option>
        <option value="se">Sweden news</option>
        <option value="ch">Switzerland news</option>
        <option value="tw">Taiwan news</option>
        <option value="th">Thailand news</option>
        <option value="tr">Turkey news</option>
        <option value="ae">United Arab Emirates news</option>
        <option value="ua">Ukraine news</option>
        <option value="ve">Venuzuela news</option>
      </select>
      <select v-model="category">
        <option value="business">Business</option>
      </select>
      <button type="submit">Get News</button>
    </form>
    <ul v-if='results'>
      <li v-for='article in results.articles'>
        {{article.title}}, {{article.publishedAt}}
        <br>
        {{article.description}}
        <br><br>       
        {{article.url}}
        <br><br>
      </li>
    </ul>

  </div>

</template>

<script>

import axios from 'axios';
export default {


  name: 'HelloWorld',
  data () {
    return {
      results: null,
      country: "us",
      category: "business"
      //us and business can be left blank. default.
    
    }
  },

  methods: {
    getNews: function() {
      axios.get('https://newsapi.org/v2/top-headlines', {
        params: {
          country: this.country,
          category: this.category,
          //sources: 'the-new-york-times',
          apiKey: 'a118ce75a5784acc9f5b0f2398d9371e'
          }
      })
      .then( response => {
        this.results = response.data;
        })
        .catch( error => {
          this.errors.push(error);
        })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ol {
  list-style-type: katakana-iroha;
  width: 40%;
  margin: auto;
}

li {
  display: list-item;
  text-align: left;
  margin: 0px 30px 0px 50px;
}

a {
  color: #42b983;
}
</style>
