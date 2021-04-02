<template>
  <div>
    <form @submit.prevent="modifyIdea">
      <div class="form-group">
        <label>Idea title:</label>
        <input placeholder="Your idea title" v-model="newName">
      </div>

      <div class="form-group">
        <label>Idea description:</label>
        <textarea placeholder="Your idea description" rows="4" cols="55" v-model="newDescription"/>
      </div>
      <button type="submit">Modify idea</button>
      <button v-on:click="abortModify">Cancel</button>
    </form>
  </div>
</template>

<script>

export default {
  name: "ModifyIdea",
  props: {
    idea: Object
  },
  data() {
    return {
      newName: this.$props.idea.name,
      newDescription: this.$props.idea.description
    }
  },
  methods: {
    modifyIdea: function () {
      this.$props.idea.name = this.newName
      this.$props.idea.description = this.newDescription
      this.$props.idea.modify = false
    },
    abortModify: function () {
      this.$props.idea.modify = false
    }
  }
}
</script>

<style scoped>

</style>
