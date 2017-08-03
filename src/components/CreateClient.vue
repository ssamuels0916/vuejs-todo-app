<template>
  <div class='ui basic content center aligned segment'>
    <button class='ui basic button icon' v-on:click="openForm" v-show="!isCreating">
      <i class='plus icon'></i>
    </button>
    <div class='ui centered card' v-show="isCreating">
      <div class='content'>
        <div class='ui form'>
          <div class='field'>
            <label>Client Name</label>
            <input v-model="nameText" type='text'>
          </div>
          <div class='field'>
            <label>Client Assets</label>
            <input v-model="assetsText" type='text'>
          </div>
          <div class='ui two button attached buttons'>
            <button class='ui basic blue button' v-on:click="sendForm()">
            Create
            </button>
            <button class='ui basic red button' v-on:click="closeForm()">
            Remove
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        nameText: '',
        assetsText: '',
        isCreating: false,
      };
    },
    methods: {
      openForm() {
        this.isCreating = true;
      },
      closeForm() {
        this.isCreating = false;
      },
      sendForm() {
        if (this.nameText.length > 0 && this.assetsText.length > 0) {
          const name = this.nameText;
          const assets = this.assetsText;

          this.$emit('add-client', {
            name,
            assets,
            assigned: false,
          });
          this.nameText = '';
          this.assetsText = '';
          this.isCreating = false;
        }
      },
    },
  };
</script>

<style>

</style>
