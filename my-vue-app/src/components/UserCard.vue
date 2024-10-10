<template>
  <div :class="userCardClass">
    <h2>{{ userData.firstName }} {{ userData.lastName }}</h2>
    <p>{{ userData.position }}</p>
    <p v-if="userData.age > 18">Age: {{ userData.age }}</p>
    <ul>
      <li v-for="hobby in userData.hobbies" :key="hobby">{{ hobby }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    userData: Object
  },
  computed: {
    userCardClass() {
      return this.userData.age > 18 ? 'user-card adult' : 'user-card'
    }
  }
}
</script>

<style scoped>
.user-card {
  border: 1px solid #ccc;
  padding: 20px;
  margin: 10px;
  border-radius: 10px;
  text-align: center;
}
.user-card.adult {
  background-color: lightgreen;
}
</style>
