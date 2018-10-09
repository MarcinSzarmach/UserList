<template>
    <div class="addUser">
        <div>
            <span>Add user section</span>
        </div>
        <div class="boxAdd" @keyup.enter="addUser">
            <input type="text" v-model="name.value" id="name" placeholder="name"> 
            <input type="text" v-model="username.value" id="username" placeholder="username">
            <input type="email" v-model="email.value" id="email" placeholder="email">
            <input type="number" v-model="phone.value" id="phone" placeholder="phone">
            <input type="text" v-model="website.value" id="website" placeholder="website">
        </div>
    <button @click=addUser>Add user</button>
    </div>
</template>

<script>
export default {
  name: "addUser",
  data: () => {
    return {
      id: {
        value: ""
      },
      name: {
        value: ""
      },
      username: {
        value: ""
      },
      email: {
        value: ""
      },
      phone: {
        value: ""
      },
      website: {
        value: ""
      }
    };
  },
  methods: {
    addUser: function() {
      let id = this.$parent.list.length + 1; // tutaj można napisać dodatkowo funkcję która będzie szukała unikalnego id dla nowego użytkownia aby id nie zostały powielone
      this.$parent.list.push({
        id: id,
        name: this.name.value,
        username: this.username.value,
        email: this.email.value,
        phone: this.phone.value,
        website: this.website.value
      });
      this.clearInputsAddUser();
    },
    clearInputsAddUser: function() {
      this.id.value = "";
      this.name.value = "";
      this.username.value = "";
      this.email.value = "";
      this.phone.value = "";
      this.website.value = "";
    }
  }
};
</script>