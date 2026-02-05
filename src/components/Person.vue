<template>
    <div class="person">
      <h2>姓名：{{ person.name }}</h2>
      <h2>年龄：{{ person.age }}</h2>
      <h2>汽车：{{ person.car.c1 }}、{{ person.car.c2 }}</h2>
      <button @click="changeName">修改姓名</button>
      <button @click="changeAge">修改年龄</button>
      <button @click="changeC1">修改车1</button>
      <button @click="changeC2">修改车2</button>
      <button @click="changeCar">修改整辆车</button>
      
    </div>
</template>

<script lang="ts" setup name="Person"> 
    import {reactive,watch} from 'vue'
    let person = reactive({
        name:'张三',
        age:18,
        car:{
            c1:'aa',
            c2:'11'
        }
    })
    function changeName(){
        person.name += "~"
    }
    function changeAge(){
        person.age += 1
    }
    function changeC1(){
        person.car.c1 = 'bb'
    }
    function changeC2(){
        person.car.c2 = '22'
    }
    function changeCar(){
        person.car = {c1:'cc',c2:'33'}
    }

    watch(()=>[person.name,person.car],(newValue,oldValue)=>{
        console.log("name,car改变！",newValue,oldValue)
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