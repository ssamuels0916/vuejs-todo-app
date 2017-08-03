<template>
  <div id="app">
    <img src="./assets/logo.png">
    <client-list v-bind:clients="clients"></client-list>
    <create-client v-on:add-client="addClient"></create-client>
  </div>
</template>

<script>
import ClientList from './components/ClientList';
import CreateClient from './components/CreateClient';


export default {
  name: 'app',
  components: {
    ClientList, CreateClient,
  },
  data() {
    return {
      clients: [{
        name: 'Andrew',
        assets: '$100000',
        city: 'Vancouver',
        assigned: false,
      }, {
        name: 'Hope',
        assets: '$1000000',
        city: 'Tottenham',
        assigned: true,
      }, {
        name: 'Sloane',
        assets: '$1000',
        assigned: false,
      }, {
        name: 'Aubrey',
        assets: '$100',
        assigned: false,
      }, {
        name: 'Carlson',
        assets: '$156000000',
        assigned: true,
      }],
    };
  },
  methods: {
    addClient(client) {
      /* eslint-disable */

        console.log(client);

      /* eslint-disable */
      this.clients.push(client);
    },
  },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
