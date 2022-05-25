<template>
  <h4>Add Project</h4>
  <form class="add_project" @submit.prevent="addProject">
    <div>
      <label>Title</label>
      <input v-model="title" type="text" required />
    </div>
    <div>
      <label>Detail</label>
      <textarea v-model="detail"></textarea>
    </div>
    <div>
      <button>Save</button>
    </div>
  </form>
</template>

<script>
export default {
    data(){
        return{
            title: '',
            detail:''
        }
    },
    methods:{
        addProject(){
           let data = {
               title: this.title,
               details: this.detail,
               complete: false
           }
           fetch('http://localhost:3000/projects', {
               method: 'POST',
               headers: {'Content-Type': 'application/json'},
               body: JSON.stringify(data)
               
           })
           .then(()=> {
               this.$router.push('/')
           })
           .catch(err => console.log(err))
        }
    }

};
</script>

<style>
.add_project {
  background: #fff;
  padding: 20px;
  border-radius: 5px;
}

.add_project > div {
  display: flex;
  flex-flow: column;
}

.add_project > div > label {
  color: #7a7a7a;
  font-weight: normal;
  font-size: 14px;
  margin-top: 7px;
}

.add_project > div > input[type="text"] {
  border: 1px solid #c3c3c3;
  padding: 7px;
  border-radius: 2px;
  margin-top: 2px;
}

.add_project > div > textarea {
  border: 1px solid #c3c3c3;
  border-radius: 3px;
  margin: 6px 0 16px;
  height: 104px;
}

.add_project > div button {
  color: white;
  display: inline-block !important;
  max-width: 130px;
  margin: 0 auto;
  padding: 10px 18px;
  text-transform: uppercase;
  border: 0;
  background: #8bc34a;
  border-radius: 4px;
  transition: all ease 0.5s;
  cursor: pointer;
}

.add_project > div button:hover {
  background: #009688;
}
</style>
