<template>
  <div>
    <div v-for="idea in ideas" v-bind:key="idea.name">
      <h3>{{idea.name}}</h3>
      <div>{{idea.description}}</div>
      <div class="comment" v-for="comment in idea.comments" v-bind:key="comment">
        <p>{{comment.comment}}</p>
      </div>
    </div>

    <div>
      <form id="newIdeaForm">
        <div>
          <label>Idea title:</label>
          <input placeholder="Your idea title">
        </div>

        <div>
          <label>Idea description:</label>
          <textarea placeholder="Your idea description" rows="4" cols="55"/>
        </div>
        <button type="submit">Add idea</button>
      </form>
    </div>

  </div>
</template>

<script>
export default {
  name: "Idea",
  data() {
    return {
      ideas: [
        { name: "Make a sandwich", description: "Because I'm hungry",
          comments: [
            {comment: "Good idea!"}
          ]},
        { name: "Watch football match", description: "Because I'm Atletico Madrid fan", comments: []}
      ]
    }
  },
  methods: {
    addIdea: function () {

    }
  }
}
</script>

<style scoped>

</style>
