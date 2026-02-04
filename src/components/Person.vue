<template>
    <div class="person">
        姓：<input type="text" v-model="firstname"> <br>
        名：<input type="text" v-model="lastname"> <br>
        <button @click="changeFullname">修改全名为lisi</button> <br>
        全名：<span>{{ fullname }}</span> <br>
    </div>
</template>

<script lang="ts" setup name="Person">
   import {ref,computed} from 'vue'

   let firstname = ref('zhang')
   let lastname = ref('san')

//    let fullname = computed(()=>{
//     return firstname.value.slice(0,1).toUpperCase() + firstname.value.slice(1) +'-'+lastname.value
//    })
    let fullname = computed({
        get(){
            return firstname.value.slice(0,1).toUpperCase() + firstname.value.slice(1) +'-'+lastname.value
        },
        set(val){
            const [str1,str2] = val.split('-')
            firstname.value = str1
            lastname.value = str2
        }
    })

    function changeFullname(){
        fullname.value = 'li-si'
    }
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