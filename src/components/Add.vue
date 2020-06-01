<template>
    <div id="Add">
        <form class="form" @submit.prevent=" () => { add(name), name = ''}">
            <input v-model="name" type="text" required>
            <button type="submit" > + </button>
        </form>
    </div>
</template>

<script>
export default {
    props:['tasks'],
    data(){
        return{
            name:''
        }
    },
    methods:{
        add(name){
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
    }
}
</script>

<style>
    #Add{
        margin-top: 25px;
    }

    .form input {
        border: solid 1px lightgray;
    }

    .form button{
        border: solid 1px lightgray;
        background-color: lightgreen;
    }
</style>