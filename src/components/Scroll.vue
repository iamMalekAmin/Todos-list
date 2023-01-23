<script>
import {ref} from 'vue'
export default{
    setup(){
        const todos = ref([])
        const newtodo = ref('')


        function create(){
            if(newtodo.value !=''){
            todos.value.push({
                id: Date.now(),
                content: newtodo.value,
                completed: false
            })
            newtodo.value='';
        }}

        function remove(item){
            todos.value.splice(todos.value.indexOf(item), 1)

        }

        return{
            todos,
            newtodo,
            create,
            remove
        }
    }
}
</script>        



<template>
    <div class="container " style="min-height: 71vh;">
        <div class="card">
  <h5 class="card-header text-center">قائمة المهام</h5>
  <div class="card-body">
    <h5 class="card-title text-center">اكتب المهمة الجديدة</h5>
    <form @submit.prevent="create" class="text-center">
        <input v-model="newtodo" type="text" class="form-control" ><br>
    <a @click="create" class="mt-4 mb-4 btn btn-primary ">اضافة</a>
    </form>
    <ul>
        <li v-for="item in todos" :key="item.id">
            <h3 class="text-center">{{ item.content }}</h3>
            <button @click="remove(item)" class="btn btn-outline-danger">احذف</button>
        <hr></li>
    </ul>
  </div>
</div>
    </div>
    
</template>
