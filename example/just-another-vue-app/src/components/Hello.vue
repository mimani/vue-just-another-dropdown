<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>which features just another dropdown</h2>
    <ul>
      <li><a href="https://www.npmjs.com/package/vue-just-another-dropdown" target="_blank">NPM Package</a></li>
      <li><a href="https://github.com/mimani/vue-just-another-dropdown" target="_blank">Code</a></li>
      <li><a href="http://stackoverflow.com/search?q=vue+just+another+dropdown" target="_blank">StackOverflow</a></li>
      <br>
    </ul>
    <h2>Ta Da</h2>
    <Dropdown :options="cities" v-model="city" placeholder="City" style="width: 30%"/>
  </div>
</template>

<script>
import vue from 'vue';
import Dropdown from 'vue-just-another-dropdown';

vue.component('Dropdown', Dropdown);

export default {
  name: 'hello',
  data() {
    return {
      msg: 'Welcome to Just Another Vue.js App',
      cities: ['Bengaluru', 'Delhi', 'Kolkata', 'Bareilly'],
      city: '',
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
