<template>
  <div class="hello">
    <ul>
      <li v-for="(item, index) in list" :key="index">
        <user v-bind:index=index v-on:on-delete="userDeleted(index)" v-bind:user=item />
      </li>
    </ul>
    <button class="delAll" @click=deleteAllUsers>Delete All</button>
    <addUser/>
  </div>
</template>

<script>
import user from './user.vue'
import addUser from './addUser.vue'

export default {
  name: "userList",
  props: {
    url: String
  },
  components: {
    user,
    addUser
  },
  data: () => {
    return {
      list: []
    };
  },
  methods: {
    deleteAllUsers: function() {
      this.list = [];
    },
    getUsers: function() {
      fetch(this.url).then(response => {
        response.json().then(data => {
          this.list = data;
        });
      });
    },
    userDeleted: function(index) {
      this.$delete(this.list,index);
    }
  },
  created: function() {
    this.getUsers();
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  max-width: 1040px;
  display: flex;
  justify-content: center;
  margin: 0 auto;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}

.addUser {
  margin-top: 25px;
  width: 100%;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
  display: flex;
  flex-wrap: wrap;
  width: 100%;
}

li {
  width: 100%;
}

a {
  color: #061a11;
}
</style>