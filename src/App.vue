<script>
import FriendComponent from './components/FriendComponent.vue'

export default {
  components: {
    FriendComponent
  },
  methods: {
    addFriend() {
      const friendId = this.friends.length + 1
      const newFriend = {
        id: friendId,
        name: "Test",
        email: "test@localhost.com",
        phone: "123456",
        image: "some-image"
      }
      this.friends.push(newFriend)
    },
    deleteFriend(id) {
      const index = this.friends.findIndex(f => f.id === id)
      this.friends.splice(index, 1)
    }
  },
  data() {
    return {
      friends: [{
        id: 1,
        name: "Manuel Lorenz",
        email: "manuel@localhost.com",
        phone: "12345",
        image: "some-image"
      },
      {
        id: 2,
        name: "Test",
        email: "test@localhost.com",
        phone: "1234657",
        image: "some-image"
      }
      ]
    }
  }
}

</script>

<template>
  <header>
    <h1>FriendList {{friends.length}}</h1>
    <button @click="this.addFriend">Add a Friend</button>
  </header>
  <ul v-for="friend in friends" :key="friend.id">
      <li>
       <FriendComponent @delete="this.deleteFriend" :image="friend.image" :name="friend.name" :email="friend.email" :phone="friend.phone" :id="friend.id"/>     
      </li>
  </ul>
 </template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
