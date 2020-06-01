<template>
    <div id="ProgressBar">
        	<span>Concluido {{progress}}%</span>
        	<div class="bar">
            	<div class="progress" :style="{width: progress + '%'} ">
            	</div>
        	</div>
    	</div>
</template>

<script>
export default {
    props:['progress']
}
</script>

<style>
    #ProgressBar{
        display: inline;
    }
    .bar{
        width: 600px;
        height: 20px;
        border: solid 2px #fff2;
        border-radius: 10px;
    }
    .progress{
        background-color: #32CD35;
        border-radius: 10px;
    }
</style>