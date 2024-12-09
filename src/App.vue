<script setup>
//importar o ref ()
import {ref} from "vue"
// deixa varias variáveis reativas
const todoList = ref(["Entregar o desafio Starbucks", "Estudar Vue.js", "Treinar", "Fazer comida", "Tomar o pré treino", "Tomar banho" ])


// variavel para armazenar uma nova tarefa
const novaTarefa = ref("");

//função para remover cada item
function removerTarefa(index) {
  todoList.value.splice(index, 1)
  // Remove 1 item pela posição clicada
}

//função para adicionar
function adicionarTarefa () {
  if(novaTarefa.value.trim()!== ""){
    todoList.value.push(novaTarefa.value.trim())
    novaTarefa.value = ""

  }
}

</script>

<template>
  <h1>📝 Lista de Tarefas</h1>
  <div v-if="todoList.length ===0">
    <p>Parabéns! Você completou todas as tarefas! 🎉 </p>
  </div>
  <ul v-else>
    <!-- v-for é uma diretiva que serve para fazer loops-->
    <li v-for="(todo, index) in todoList" :key="index"> {{ todo }}
      <button @click="removerTarefa(index)">❌ Remover</button>
    
    </li>
  </ul>

  <section>
    <input type="text"
    placeholder="Digite uma nova tarefa"
    v-model="novaTarefa"
    >
    <!-- A diretiva v-model, sincroniza o valor de uma variável ao input-->
     <button @click="adicionarTarefa">Adicionar tarefa</button>
  </section>

</template>