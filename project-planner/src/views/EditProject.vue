<template>
  <h1>Edit project</h1>
  <form @submit.prevent="handleSubmit">
    <label>Title:</label>
    <input type="text" required v-model="title" />
    <label>Details:</label>
    <textarea required v-model="details"></textarea>
    <button>Update project</button>
  </form>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
      title: "",
      details: "",
      uri: "http://localhost:3000/projects/" + this.id,
    };
  },
  mounted() {
      fetch(this.uri)
      .then(res=>res.json())
      .then(data=>{
          this.title= data.title, this.details=data.details
      })
  },
  methods:{
      handleSubmit(){
          fetch(this.uri,{
              method:'PATCH',
              headers:{'content-Type':'application/json'},
              body:JSON.stringify({title:this.title, details:this.details})
          }).then(()=>{
              this.$router.push('/')
          }).catch(err=>console.log(err.message))
      }
  }
};
</script>

<style></style>
