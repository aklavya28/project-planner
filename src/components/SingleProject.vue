<template>
  <div class="project" :class="{complete: project.complete  }">
    <div class="title" >
      <h3 @click="showdetail">{{ project.title }}</h3>
      <div>
        <router-link :to="{ name:'EditProject', params:{id:project.id} }">

        <span class="material-icons">edit</span>
        </router-link>
        <span @click="deteteProject" class="material-icons">close</span>
        <span  @click="complete" class="material-icons tick">done</span>
      </div>
    </div>
    <div v-if="detail" class="detail">
      <p>{{ project.details }}</p>
    </div>
  </div>
</template>
<script>
export default {
  props: ["project"],
  data() {
    return {
      detail: false,
      uri: 'http://localhost:3000/projects/'+this.project.id
    };
  },
  methods: {
    showdetail() {
      this.detail = !this.detail;
    },
    deteteProject(){
        fetch(this.uri,{method: 'DELETE'})
        .then(()=> this.$emit('delete', this.project.id))
        .catch(err=>console.log(err));
     
    },
    complete(){
        fetch(
            this.uri, 
             {
                 method: 'PATCH',
                 headers: {'Content-Type': 'application/json'},
                 body: JSON.stringify({complete: !this.project.complete})
             }
        )
        .then(()=>this.$emit('complete', this.project.id))
        .catch(err=>console.log(err))
    }
  },
};
</script>
<style scoped>
.project {
  padding: 15px 10px;

  border-left: 4px solid rgb(252, 3, 103);
  display: flex;
  flex-flow: column;
  padding: 20px 10px;
  margin-bottom: 10px;
  box-shadow: 0 0 10px #d9d9d9;
  border-radius: 3px;
  background: #fff;
}
.project > .title h3 {
  margin: 0;
  text-transform: capitalize;
  font-weight: 600;
  cursor: pointer;
  width: 100%;
}

.project > .detail p {
  margin: 9px 15px;
}
.title {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 10px;
}

.title > div {
  display: flex;
  gap: 8px;
}

.title > div span {
  transition: all ease 0.5s;
  color: #9f9f9f;
  cursor: pointer;
}

.title > div span:hover {
  color: #424242;
}
.project.complete {
    border-color: #5cc15c;
}
.project.complete  .tick{
   color: #5cc15c;
}
</style>
