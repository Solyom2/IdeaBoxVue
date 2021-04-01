<template>
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
</template>

<script>
export default {
name: "NewIdea"
}
</script>

<style scoped>

</style>
