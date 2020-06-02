<template>
	<div id="app">
		<h1>Tarefas</h1>
		<ProgressBar :progress="progressBar" />
		<Add @addTask="addTask" /> 
		<div class="tarrefas">
			<Tarrefas :tasks="tasks" @deleteTask="deleteTask" />
		</div>
	</div>
</template>

<script>
import Add from './components/Add'
import Tarrefas from './components/Tarrefas'
import ProgressBar from './components/ProgressBar'
export default {
	components:{
		Add,
		Tarrefas,
		ProgressBar
	},
	data(){
		return{
			tasks: [],
		}
	},
	methods:{
		deleteTask(i){
			this.tasks.splice(i,1)
		},
		addTask(name){
            const task = {
                name:'',
                status: false
            }
            const aux = this.tasks.filter(t => t.name === name).length
            task.name = name

            if(aux === 0){
                this.tasks.push(task)

            }
            else{
                alert('A tarrefa já existe.')
            }
        },
	},
	computed:{
		progressBar(){
			const total = this.tasks.length
			const done = this.tasks.filter(t => t.status === true ).length

			return Math.round( done / total * 100) || 0
		}
	}
}
</script>

<style>
	body {
		font-family: 'Lato', sans-serif;
		background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
		color: #FFF;
	}

	#app {
		display: flex;
		flex: 1;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		height: 100vh;
	}

	#app h1 {
		margin-bottom: 5px;
		font-weight: 300;
		font-size: 3rem;
	}
	.tarrefas{
		display: flex;
		flex-direction: row;
		justify-content:center;
	}
	#ProgressBar{
        display: inline;
    }
    .bar{
        width: 600px;
        height: 20px;
        border: solid 1px white;
    }
    .progress{
        background-color: #32CD32;
        height: 100%;
        width: 80%;
    }
</style>
