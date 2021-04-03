<template>
  <div>
    <form @submit.prevent="modifyIdea">
      <div class="form-group">
        <input placeholder="Your idea title" v-model="newName">
      </div>

      <div class="form-group">
        <textarea placeholder="Your idea description" rows="4" cols="55" v-model="newDescription"/>
      </div>
      <button type="submit" class="btn-success mr-1">Modify idea</button>
      <button v-on:click="abortModify" class="btn-danger mr-1">Cancel</button>
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
      if(this.newName === "" || this.newName === null) {
        window.alert("Idea title can't be empty")
        return
      }
      else if(this.newDescription === "" || this.newDescription === null) {
        window.alert("Idea description can't be empty")
        return
      }
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
