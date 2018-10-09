<template>
    <div class="user"> 
        <span>
            {{ user.id }} 
        </span>
        <span>
            {{ user.email }} 
        </span>
        <span>
            {{ user.username }} 
        </span>
        <span>
            {{ user.phone }} 
        </span>
        <a target="_blank" :href="'https://'+user.website">
            {{ user.website }}
        </a>
        <button @click=deleteUser(index)>Delete this</button>
    </div>
</template>

<script>
export default {
  name: "user",
  props: {
    index: Number,
    user: Object
  },
  methods: {
    deleteUser: function(index) {
      this.$emit('on-delete',index)  
    }
  }
};
</script>

<style scoped>
.user {
  display: flex;
  margin: 0 10px;
  width: 100%;
  justify-content: space-between;
  transition: all .2s ease;
  border: 1px solid transparent;
}
.user:hover{
  border: 1px solid grey;
}
.user a,
.user span{
  width: 100%;
  text-align: center;
}
</style>

