<template>
  <div class="mb-5">
    <div class="mt-10 mb-2 border-bottom border-success" v-for="idea in ideas" v-bind:key="idea.name">
      <div v-if="!idea.modify">

        <h1 class="font-weight-bold">{{idea.name}}</h1>
        <p class="font-italic">Created: {{idea.date}}</p>
        <h4 class="font-weight-bolder">Description</h4>
        <p class="description">{{idea.description}}</p>

        <h4 class="font-weight-bolder">Comments</h4>
        <div class="comment" v-for="comment in idea.comments" v-bind:key="comment">
          <p class="font-italic mb-0">{{comment.date}}</p>
          <p>{{comment.comment}}</p>
        </div>
      </div>

      <ModifyIdea class="mt-3" v-if="idea.modify" :idea="idea"/>

      <div class="mb-4">
        <button v-on:click="modifyIdea(idea)" v-if="!idea.edit && !idea.modify" class="btn-secondary mr-1">Modify idea</button>
        <button v-on:click="removeIdea(idea)" v-if="!idea.edit && !idea.modify" class="btn-danger mr-1" >Delete idea</button>
        <button v-on:click="writeComment(idea)" v-if="!idea.edit && !idea.modify" class="mr-1">Write comment</button>
      </div>

      <WriteComment class="mb-2" v-if="idea.edit" :idea="idea"/>
    </div>

    <NewIdea/>
  </div>
</template>

<script>
import WriteComment from "@/components/WriteComment";
import NewIdea from "@/components/NewIdea";
import ModifyIdea from "@/components/ModifyIdea";

export default {
  name: "Idea",
  components: {
    WriteComment, NewIdea, ModifyIdea
  },
  data() {
    return {
      ideas: [
        { name: "Make a sandwich", description: "Because I'm hungry", edit: false, modify: false, date: new Date().toLocaleString(),
          comments: [
            {comment: "Good idea!", date: new Date().toLocaleString()}
          ]},
        { name: "Watch football match", description: "Because I'm Atletico Madrid fan", edit: false,  modify: false, date: new Date().toLocaleString(),
          comments: []}
      ]
    }
  },
  methods: {
    writeComment: function (idea) {
      idea.edit = true
    },
    removeIdea: function (idea) {
      this.ideas = this.ideas.filter(i => i != idea)
    },
    modifyIdea: function (idea) {
      idea.modify = true
    }
  }
}
</script>

<style scoped>

</style>
