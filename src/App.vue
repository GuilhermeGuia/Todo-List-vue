<template>
  <div id="app">
    <div class="container">
      <header>
        <h1>To-Do-List</h1>
        <button class="excluir" v-on:click="excluirTodasTarefas">Excluir</button>
      </header>
      <main>
        <div class="box-adicionar">
          <input v-model="inputTask" type="text">
          <button class="adicionar" v-on:click="adicionar"><span>+</span></button>
        </div>
        <div class="listas">
          <div class="elementos" v-for="tarefa in tarefas" :key="tarefa.task">
            <div class="input-box" >
              <label class="input-checkbox">
                <input type="checkbox" >
                <span class="checkmark"></span>
              </label>
              <p>{{tarefa.task}}</p>
            </div>
            <button class="excluir-elemento">Excluir</button>
          </div>
        </div>
      </main>
    </div>

  </div>

</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      tarefas: [
      ],
      inputTask: ''
    }
  },
  created(){
    document.addEventListener('keyup', )
  },
  methods: {
    adicionar(){
      if (this.inputTask.trim() === '') return;

      this.tarefas.push(
        {task: this.inputTask.trim()}
      )
      this.limparInput();
    },
    limparInput() {
      this.inputTask = '';
    },
    excluirTodasTarefas() {
      this.tarefas = [];
    }
  }

}
</script>

<style>
 .input-checkbox {
  display: block;
  position: relative;

  cursor: pointer;
}

/* Hide the browser's default checkbox */


/* Create a custom checkbox */
.checkmark {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  left: 0;
  height: 30px;
  width: 30px;
  background-color: #eee;
}

/* On mouse-over, add a grey background color */
.input-checkbox:hover input~.checkmark {
  background-color: #ccc;
}

/* When the checkbox is checked, add a blue background */
.input-checkbox input:checked~.checkmark {
  background-color: #2196F3;
}

/* Create the checkmark/indicator (hidden when not checked) */
.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

/* Show the checkmark when checked */
.input-checkbox input:checked~.checkmark:after {
  display: block;
}

/* Style the checkmark/indicator */
.input-checkbox .checkmark:after {
  left: 9px;
  top: 5px;
  width: 5px;
  height: 10px;
  border: solid white;
  border-width: 0 3px 3px 0;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: #f2f2f2;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

a {

  text-decoration: none;
}

#app {


  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}

.container {
  max-width: 900px;
  width: 90%;
  margin: auto;
}

main {
  width: 100%;
}


button,
a {
  display: block;
  cursor: pointer;
}

header {
  background-color: #fff;
  position: relative;
  padding: 1.5rem;
  border-bottom: 2px solid #dad8d8;
}

h1 {
  text-align: center;
}

.excluir {
  position: absolute;
  right: 20px;
  top: 50%;
  transform: translateY(-50%);
  display: inline-block;

  border: 0;
  outline: 0;

  color: #fff;
  font-size: 1.2rem;
  background-color: #c81e1e;
  padding: 1rem 1.5rem;
  border-radius: 5px;
}
.listas {
  overflow:scroll;
  height: 400px;
}
.box-adicionar,
.elementos {
  background-color: #bcbaba;
  margin-top: 1.2rem;
  border-radius: 5px;
  display: flex;
  justify-content: space-between;
  padding: 0.5rem;
}

.box-adicionar input {
  width: 85%;
  outline: 0;
  border: 0;
  font-size: 2rem;
  padding: 0.9rem;
}

.box-adicionar .adicionar {
  background-color: #2196F3;
  border: 0;
  text-align: center;
  padding: 1rem 2rem;
  border-radius: 50%;
  margin-right: 10px;
}

.adicionar span {
  font-size: 3rem;

  color: #fff;
}

.input-box {
  display: flex;
  align-items: center;
  margin-left: 2rem;
  gap: 2rem;
}

p {
  font-size: 1.5rem;
}

.input-box input {
  background-color: red;
}

.excluir-elemento {
  border: 0;
  outline: 0;

  color: #fff;
  font-size: 1.2rem;
  background-color: #c81e1e;
  padding: 1rem 1.5rem;
  border-radius: 5px;
}
</style>
