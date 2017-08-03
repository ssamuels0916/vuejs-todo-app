<template>
  <div>
    <p>Assigned clients: {{clients.filter(client => {return client.assigned === true}).length}}</p>
    <p>Unassigned clients: {{clients.filter(client => {return client.assigned === false}).length}}</p>
    <!--   // we are now passing the data to the todo component to render the todo list-->
    <client v-on:delete-client="deleteClient" v-for="client in clients" v-bind:client="client" v-bind:key="client.id"></client>
  </div>
</template>

<script>
import Client from './Client';
import CreateClient from './CreateClient';

export default {
  props: ['clients'],
  components: {
    Client, CreateClient,
  },
  methods: {
    deleteClient(client) {
      const clientIndex = this.clients.indexOf(client);
      this.clients.splice(clientIndex, 1);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  ul {
    list-style: none;
  }
</style>
