<template>
  <div>
    <div v-for="idea in ideas" v-bind:key="idea.name">
      <h3>{{idea.name}}</h3>
      <div>{{idea.description}}</div>
      <div class="comment" v-for="comment in idea.comments" v-bind:key="comment">
        <p>{{comment.comment}}</p>
      </div>

      <button v-on:click="removeIdea(idea)" v-if="!idea.edit">Delete idea</button>
      <button v-on:click="writeComment(idea)" v-if="!idea.edit">Write comment</button>
      <WriteComment v-if="idea.edit" :idea="idea"/>
    </div>

    <NewIdea/>

  </div>
</template>

<script>
import WriteComment from "@/components/WriteComment";
import NewIdea from "@/components/NewIdea";

export default {
  name: "Idea",
  components: {
    WriteComment, NewIdea
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
    }
  },
  methods: {
    writeComment: function (idea) {
      idea.edit = true;
    },
    removeIdea: function (idea) {
      this.ideas = this.ideas.filter(i => i != idea)
    }
  }
}
</script>

<style scoped>

</style>
