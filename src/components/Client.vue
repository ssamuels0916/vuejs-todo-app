<template>
  <div class='ui centered card'>
    <div class='content' v-show="!isEditing">
      <div class='header'>
        {{client.name}}
      </div>
      <div class='meta'>
        {{client.assets}}
        {{client.city}}
      </div>
      <div class='extra content'>
        <span class='right floated edit icon' v-on:click="showForm">
          <i class='edit icon'></i>
        </span>
        <!-- add trash icon to delete client -->
        <span class='right floated trash icon' v-on:click="deleteClient(client)">
          <i class='trash icon'></i>
        </span>
      </div>
    </div>
    <!-- form is visible when we're in editing mode -->
    <div class="content" v-show="isEditing">
      <div class='ui form'>
        <div class='field'>
          <label>Name</label>
          <input type='text' v-model="client.name">
        </div>
        <div class='field'>
          <label>Assets</label>
          <input type='text' v-model="client.assets">
        </div>
        <div class='ui two button attached buttons'>
          <button class='ui basic blue button' v-on:click="hideForm">Close x</button>
        </div>
      </div>     <!-- form is visible when we're in editing mode -->
    </div>
    <div class='ui bottom attached green basic button' v-show='!isEditing && client.assigned'>Assigned</div>
    <div class='ui bottom attached red basic button' v-show='!isEditing && !client.assigned'>Not Assigned</div>
  </div>
</template>
<script>

export default {
  props: ['client'],
  data() {
    return {
      isEditing: false,
    };
  },
  methods: {
    showForm() {
      this.isEditing = true;
    },
    hideForm() {
      this.isEditing = false;
    },
    deleteClient(client) {
      this.$emit('delete-client', client);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
