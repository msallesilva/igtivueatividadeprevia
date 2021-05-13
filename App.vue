<template>
  <div>
  <h1>!!! Minhas Tarefas !!!</h1>

    <button @click="()=>{showList = !showList}">Ver as tarefas</button>
    <br>
    <br>
    <ul v-if=showList>
      <li v-for="task in tasks"
        :key="task"
      >
        {{task.activity}}
      </li>
    <p>Total de {{tasks.length}} Atividades</p>
    </ul>

    <p v-else >Clique para ver as Tarefas</p>

  </div>
</template>

<script>
export default {
  
  data:()=>({
    nome:'Marco',
    showList:false,
    tasks:[
      {activity: 'Jogar Bola', isDone:false},
      {activity: 'Viajar', isDone:false}
    ]
  })
  
}
</script>

<style>

</style>