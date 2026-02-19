<template>
    <div class="person">
      <h1>水温达到60度，水位到100cm提示</h1>
      <h2>水温：{{ temp }}°</h2>
      <h2>水位：{{ height }}cm</h2>
      <button @click="changeTemp">修改水温</button>
      <button @click="changeHeight">修改水位</button>
    </div>
</template>

<script lang="ts" setup name="Person"> 
    import {ref,watch,watchEffect} from 'vue'

    let temp = ref(0)
    let height = ref(0)

    function changeTemp(){
        temp.value += 10
    }
    function changeHeight(){
        height.value += 10
    }

    // watch([temp,height],(value)=>{
    //     let [newTemp,newHeight] = value
    //     if (newTemp >=60 || newHeight >=100){
    //         console.log("向服务器发送请求！")
    //     }
        
    // })

    watchEffect(()=>{
        if(temp.value >= 60 || height.value >=100){
            console.log("向服务器发送请求！")
        }
    })

 

</script>

<style scoped>
    .person{
        background: skyblue;
        box-shadow: 0 0 10px;
        border-radius: 10px;
        padding: 20px;
    }
    button{
        margin: 0 5px;
    }
</style>