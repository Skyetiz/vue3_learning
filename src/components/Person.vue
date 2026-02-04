<template>
    <div class="person">
      <h2>姓名：{{ person.name }}</h2>
      <h2>年龄：{{ person.age }}</h2>
      <button @click="changeName">修改姓名</button>
      <button @click="changeAge">修改年龄</button>
      <button @click="changeWhole">修改全部</button>
    </div>
</template>

<script lang="ts" setup name="Person"> 
    import {ref,watch} from 'vue'

    let person = ref({
        name: '张三',
        age: 18
    })
    function changeName(){
        person.value.name += '~'
    }
    function changeAge(){
        person.value.age += 1
    }
    function changeWhole(){
        person.value ={name:'李四',age:99}
    }
    watch(person,(newVaule,oldValue)=>{
        console.log('person变换了',newVaule,oldValue)
    },{deep:true})
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