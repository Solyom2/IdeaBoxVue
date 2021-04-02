<template>
  <div>
    <form @submit.prevent="addIdea">
      <div class="form-group">
        <label>Idea title:</label>
        <input placeholder="Your idea title" v-model="formFields.ideaName">
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
      formFields: {
        ideaName: "",
        ideaDescription: ""
      }
    }
  },
  methods: {
    addIdea: function () {
      if(this.formFields.ideaName === "" || this.formFields.ideaName === null) {
        window.alert("Idea title can't be empty")
        return
      }
      else if(this.formFields.ideaDescription === "" || this.formFields.ideaDescription === null) {
        window.alert("Idea description can't be empty")
        return
      }
      this.$parent.ideas.push({name: this.formFields.ideaName, description: this.formFields.ideaDescription, edit: false, modify: false,
        date: new Date().toLocaleString(), comments: []})
      this.formFields = {}
    }
  }
}
</script>

<style scoped>

</style>
