<template>
  <div>
    <form @submit.prevent="addIdea">
      <div class="form-group">
        <label>Idea title:</label>
        <input placeholder="Your idea title" v-model="formFields.ideaTitle">
      </div>

      <div class="form-group">
        <label>Idea description:</label>
        <textarea placeholder="Your idea description" rows="4" cols="55" v-model="formFields.ideaDescription"/>
      </div>
      <button type="submit">Add idea</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "NewIdea",
  data() {
    return {
      formFields: {}
    }
  },
  methods: {
    addIdea: function () {
      this.$parent.ideas.push({name: this.formFields.ideaTitle, description: this.formFields.ideaDescription, edit: false, modify: false, comments: []})
      this.formFields = {}
    }
  }
}
</script>

<style scoped>

</style>
