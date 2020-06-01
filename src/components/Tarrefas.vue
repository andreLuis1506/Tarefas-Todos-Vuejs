<template >
    <div id="Tarrefas">
        <div id="container" v-for=" (task, i) in tasks" :key="task.name">
            <div :class=" task.status ? 'box complete' : 'box uncomplete' " @click="modify(task)">
                <span class="close" @click.stop="$emit('deleteTask', i)">X</span>
                <p>{{task.name}}</p>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    props:['tasks'],
    methods:{
        modify(task){
            console.log('entrou')
            task.status = !task.status
            this.$emit('modified')
        }
    }
}
</script>

<style>
    #Tarrefas{
        margin-top: 30px;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        justify-content: center;
    }
    #container{
        margin-right: 10px;
        margin-top: 10px;
    }
    .box{
        position: relative;
        display: flex;
        flex: 1;
        justify-content: center;
        align-items: center;
        box-sizing: 50px;
        border-radius: 10px;
        border-left: solid 3px #fff8;
        border-bottom: solid 1px #fff8 ;
        width: 200px;
        height: 100px;
        padding: 10px;
        font-size: 20px;
        font-weight: 700;
    }
    .complete{
        background-color: #32CD32;
        text-decoration: line-through;
    }
    .uncomplete{
        background-color: #e02140;
    }
    .close{
        position: absolute;
        right: 10px;
        top: 10px;
        font-size: 0.8rem;
    }

</style>