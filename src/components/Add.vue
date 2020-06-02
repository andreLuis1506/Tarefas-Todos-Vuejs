<template>
    <div id="Add">
        <form class="form" @submit.prevent=" () => { $emit('addTask', name), name = ''}">
            <input v-model="name" type="text" required>
            <button type="submit" > + </button>
        </form>
    </div>
</template>

<script>
export default {
    data(){
        return{
            name:''
        }
    }
}
</script>

<style>
    #Add{
        margin-top: 25px;
    }

    .form input {
        background-color: #fff2;
        color: white;
        font-size: 1rem;
        padding: 4px;
        border: solid 1px white;
        border-top-left-radius: 10px;
        border-bottom-left-radius: 10px ;
    }

    .form button{
        font-size: 1rem;
        padding: 4px;
        border: solid 1px white;
        background-color: lightgreen;
        border-top-right-radius: 10px;
        border-bottom-right-radius: 10px ;
    }
</style>