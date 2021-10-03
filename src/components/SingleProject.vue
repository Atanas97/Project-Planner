<template>
  <div class="project" :class="{ complete: project.complete}">
      <div class="actions">
          <h3 @click="showDetails=!showDetails">{{project.title}}</h3>
          <div class="icons">
              <i class="fas fa-check" @click="toggleComplete"></i>
              <i class="fas fa-trash-alt" @click="deleteProject"></i>
              <router-link :to="{ name: 'EditProject', params: {id: project.id}}"><i class="fas fa-edit"></i></router-link>
          </div>
      </div>
      <div class="details" v-if="showDetails" :class="{active :showDetails}">
          {{project.details}}
      </div>
  </div>
</template>

<script>
export default {
    props: ["project"],
    data(){
        return{
            showDetails: false,
            uri: 'http://localhost:3000/projects/' + this.project.id 
        }
    },
    methods: {
        deleteProject(){
            fetch(this.uri, { method: "DELETE"})
            .then(()=> this.$emit('delete', this.project.id))
            .catch(err => console.log(err))
        },
        toggleComplete(){
            fetch(this.uri, {
                method: 'PATCH',
                headers: {'Content-Type': "application/json"},
                body: JSON.stringify({complete: !this.project.complete})
                })
            .then(() => this.$emit('complete', this.project.id))
            .catch((err)=> console.log(err))
        }
    }
}
</script>

<style>
    .project{
        margin: 20px auto;
        background: white;
        padding: 10px 20px;
        border-radius: 4px;
        box-shadow: 1px 2px 3px rgba(0,0,0,0.05);
        border-left: 4px solid #e90074;
    }

    .project.complete{
        border-left: 4px solid #00ce89;
    }
    .project.complete .fa-check{color: #00ce89;}
    h3{
        cursor: pointer;
    }
    .actions{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    .icons .fas{
        font-size: 20px;
        margin-left: 10px;
        color: #bbb;
        cursor: pointer;
    }
    .icons .fas:hover{
        color: #777;
    }
</style>