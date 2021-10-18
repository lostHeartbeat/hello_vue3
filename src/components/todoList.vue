<template>
    <div>
        <input type="text" v-model="value" @keyup.enter="addData">
        <div>进行中</div>
        <ul>
             <template v-for="(item,index) in list">
                 <li v-if="!item.checked" :key="index">
                <input type="checkbox" v-model="item.checked" @change="setTodolist" /> -----{{item.title}}----- <button @click="deleteData(index)">删除</button>
            </li>
             </template>
        </ul>
        <div>已完成</div>
         <ul>
             <!--
                当v-for与v-if一起使用时可以使用 template 
             注意：使用 template 循环时要把:key="index"放在template 里面的标签上 -->
             <template v-for="(item,index) in list">
                 <li v-if="item.checked" :key="index">
                <input type="checkbox" v-model="item.checked" @change="setTodolist" /> -----{{item.title}}----- <button @click="deleteData(index)">删除</button>
            </li>
             </template>
           
        </ul>
    </div>
</template>

<script>
import storage from "../models/storage"
    export default {
        data() {
            return {
                value:"",
                list:[]
            }
        },
        
        mounted() {
            if(storage.get("todoList") == null)return
            this.list = storage.get("todoList")
            console.log(this.list)
        },
        methods: {
            // 添加
            addData(){
                this.list.push({
                    title:this.value,
                    checked:false
                })
                this.value = ""
                storage.set("todoList",this.list)
            },
            // 删除
            deleteData(id){
                this.list.splice(id,1)
                storage.set("todoList",this.list)
            },
            // 修改状态
            setTodolist(){
                storage.set("todoList",this.list)
            }
        },
    }
</script>

<style lang="less" scoped>

</style>