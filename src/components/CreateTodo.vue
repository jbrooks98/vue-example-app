<template>
  <div class='ui basic content center aligned segment'>
    <v-btn class='ui basic button icon' @click="openForm" v-show="!isCreating">
       <v-icon dark>mdi-pencil-plus</v-icon>
    </v-btn>
    <div class='ui centered card' v-show="isCreating">
      <div class='content'>
        <div class='ui form'>
          <div class='field'>
            <label>Title</label>
            <input v-model="titleText" type='text'>
          </div>
          <div class='field'>
            <label>Project</label>
            <input v-model="projectText" type='text'>
          </div>
          <div class='ui two button attached buttons'>
            <v-btn class='ui basic blue button' @click="sendForm()">
              Create
            </v-btn>
            <v-btn class='ui basic red button' @click="closeForm">
              Cancel
            </v-btn>
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
      titleText: '',
      projectText: '',
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
      if (this.titleText.length > 0 && this.projectText.length > 0) {
        const title = this.titleText;
        const project = this.projectText;
        this.$emit('create-todo', {
          title,
          project,
          done: false,
        });
        this.titleText = '';
        this.projectText = '';
        this.isCreating = false;
      }
    },
  },
};
</script>