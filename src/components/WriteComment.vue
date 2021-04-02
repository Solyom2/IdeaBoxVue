<template>
  <div>
    <form @submit.prevent="addComment">
      <div class="form-group">
        <textarea placeholder="Write your comment here" rows="4" cols="55" v-model="newComment"/>
      </div>

      <button type="submit" class="btn-success mr-1">Add comment</button>
      <button v-on:click="abortComment" class="btn-danger mr-1">Cancel</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "WriteComment",
  props: {
    idea: Object
  },
  data() {
    return {
      newComment: ""
    }
  },
  methods: {
    abortComment: function () {
      this.newComment = ""
      this.$props.idea.edit = false
    },
    addComment: function () {
      if(this.newComment === "" || this.newComment === null) {
        window.alert("Comment field can't be empty")
        return
      }
      this.$props.idea.comments.push({comment: this.newComment, date: new Date().toLocaleString()})
      this.newComment = ""
      this.$props.idea.edit = false
    }
  }
}
</script>

<style scoped>

</style>
