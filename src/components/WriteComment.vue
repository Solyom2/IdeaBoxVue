<template>
  <div>
    <form @submit.prevent="addComment">
      <div class="form-group">
        <textarea placeholder="Write your comment here" rows="4" cols="55" v-model="newComment"/>
      </div>

      <button type="submit">Add comment</button>
      <button v-on:click="abortComment">Cancel</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "IdeaComment",
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
      this.$props.idea.comments.push({comment: this.newComment})
      this.newComment = ""
      this.$props.idea.edit = false
    }
  }
}
</script>

<style scoped>

</style>
