<template>
  <div>
    <div v-for="idea in ideas" v-bind:key="idea.name">
      <h3>{{idea.name}}</h3>
      <div>{{idea.description}}</div>
      <div class="comment" v-for="comment in idea.comments" v-bind:key="comment">
        <p>{{comment.comment}}</p>
      </div>
      <button v-on:click="writeComment(idea)" v-if="!idea.edit">Write comment</button>
      <WriteComment v-if="idea.edit" :idea="idea"/>
    </div>

    <div>
      <form @submit.prevent="addIdea">
        <div>
          <label>Idea title:</label>
          <input placeholder="Your idea title" v-model="formFields.ideaTitle">
        </div>

        <div>
          <label>Idea description:</label>
          <textarea placeholder="Your idea description" rows="4" cols="55" v-model="formFields.ideaDescription"/>
        </div>
        <button type="submit">Add idea</button>
      </form>
    </div>

  </div>
</template>

<script>
import WriteComment from "@/components/WriteComment";
import NewIdea from "@/components/NewIdea";

export default {
  name: "Idea",
  components: {
    WriteComment
  },
  data() {
    return {
      ideas: [
        { name: "Make a sandwich", description: "Because I'm hungry", edit: false,
          comments: [
            {comment: "Good idea!"}
          ]},
        { name: "Watch football match", description: "Because I'm Atletico Madrid fan", edit: false, comments: []}
      ],
      formFields: {}
    }
  },
  methods: {
    addIdea: function () {
      this.ideas.push({name: this.formFields.ideaTitle, description: this.formFields.ideaDescription, edit: false, comments: []})
      this.formFields = {}
    },
    writeComment: function (idea) {
      idea.edit = true;
    }
  }
}
</script>

<style scoped>

</style>
