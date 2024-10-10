<template>
  <div>
    <div class="toolbar">
      <button @click="filterUsers('male')">Male</button>
      <button @click="filterUsers('female')">Female</button>
      <button @click="resetFilter">All</button>
    </div>
    <div v-if="filteredUsers.length > 0">
      <UserCard v-for="user in filteredUsers" :key="user.id" :userData="user" />
    </div>
    <p v-else>Список юзерів пустий</p>
  </div>
</template>

<script>
import UserCard from './UserCard.vue';

export default {
  components: { UserCard },
  data() {
    return {
      users: [
        { id: 1, firstName: 'John', lastName: 'Doe', gender: 'male', age: 22, position: 'Developer', hobbies: ['Reading', 'Traveling'] },
        { id: 2, firstName: 'Jane', lastName: 'Doe', gender: 'female', age: 18, position: 'Designer', hobbies: ['Cooking', 'Painting'] },
        { id: 3, firstName: 'Alex', lastName: 'Smith', gender: 'male', age: 30, position: 'Manager', hobbies: ['Sports', 'Music'] },
        { id: 4, firstName: 'Emily', lastName: 'Jones', gender: 'female', age: 25, position: 'Analyst', hobbies: ['Reading', 'Swimming'] },
        { id: 5, firstName: 'Michael', lastName: 'Brown', gender: 'male', age: 35, position: 'Engineer', hobbies: ['Hiking', 'Gaming'] },
        { id: 6, firstName: 'Laura', lastName: 'Davis', gender: 'female', age: 28, position: 'Consultant', hobbies: ['Gardening', 'Writing'] },
        { id: 7, firstName: 'David', lastName: 'Wilson', gender: 'male', age: 40, position: 'Teacher', hobbies: ['Photography', 'Traveling'] },
        { id: 8, firstName: 'Linda', lastName: 'Taylor', gender: 'female', age: 32, position: 'Architect', hobbies: ['Cooking', 'Cycling'] },
        { id: 9, firstName: 'Chris', lastName: 'Moore', gender: 'male', age: 26, position: 'Sales', hobbies: ['Movies', 'Drawing'] },
        { id: 10, firstName: 'Rachel', lastName: 'Anderson', gender: 'female', age: 24, position: 'Nurse', hobbies: ['Dance', 'Crafting'] }
      ],
      genderFilter: ''
    };
  },
  computed: {
    filteredUsers() {
      if (!this.genderFilter) return this.users;
      return this.users.filter(user => user.gender === this.genderFilter);
    }
  },
  methods: {
    filterUsers(gender) {
      this.genderFilter = gender;
    },
    resetFilter() {
      this.genderFilter = '';
    }
  }
}
</script>

<style scoped>
.toolbar {
  margin-bottom: 20px;
}
button {
  margin-right: 10px;
}
</style>
