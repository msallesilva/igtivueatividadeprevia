<template>
  <div>
  <h1>!!! Minhas Tarefas !!!</h1>

    <button @click="handlesShowHideList()">Ver as tarefas</button>
    <br>
    <input 
        type="text"
        @keyup.enter="addTask" 
        v-focus
        v-model="currentTask">
    <br>

    <ul v-if=showList>
      <li v-for="task in tasks"
        :key="task"
        @dblclick="complete(task)"
        class="task-item"
        :class="{'line-through': task.isDone}"
      >
        {{task.activity}}
        <button @click="remove(task)">&times;</button>
      </li>
    <p>Total de {{tasks.length}} Atividades</p>
    </ul>

    <p v-else >Clique para ver as Tarefas</p>

  </div>
</template>

<script>
  const focus = {
    inserted: (el)=>{
      el.focus()
    }
  }
export default {
  directives :{
    focus
  },
  data:()=>({
    currentTast:'',
    nome:'Marco',
    showList:false,
    tasks:[
      {activity: 'Jogar Bola', isDone:false},
      {activity: 'Viajar', isDone:false}
    ]
  }),
  methods:{
    addTask(){
      this.tasks.push({
        activity: this.currentTask,
        isDone:false  
      })
      this.currentTask =''
    },

    remove(task){
      this.tasks = this.tasks.filter(t => t.activity !== task.activity);
    },
    handlesShowHideList(){
      this.showList = !this.showList;
    },
    complete(task){
      this.tasks = this.tasks.map(t => {
        if(t.activity === task.activity){
          return{...t, isDone: !t.isDone}
        }
        return{...t}
      })
    }
  }
}
</script>

<style>
  .line-through {
  text-decoration: line-through;
  }
  .task-item{
  cursor: pointer;
  }
</style>