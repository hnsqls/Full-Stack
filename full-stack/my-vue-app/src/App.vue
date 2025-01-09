<script setup>
import  { ref, watch } from 'vue'
import Mybutton  from './components/Mybutton.vue'
const todo = ref('')

const list = ref([
  {
    isCompleted: false,
    text:'跑步',
  },
  {
    isCompleted: false,
    text:'背单词',
  },
  {
    isCompleted: false,
    text:'学习Java',
  }
])

function add(){
  list.value.push(
    {
      isCompleted:false,
      text:todo.value
    }
  )

  todo.value=''
}

function del(index){
  list.value.splice(index,1)
}

/* 监听器*/ 
function sout (newValue,oldValue){
  console.log(newValue + oldValue)
}

watch(todo,sout)



/**
 * 动态展示
 * v-show
 * v-if
 */
const bool = ref(true)


/**接受子组件的信号 */
function accept(str){
  console.log(str)

}

</script>
<template>
<div class="top">
    <div class="text">
        <spann>hnsqls的Todo App</spann>
    </div>
    <div v-if="bool" class="todo-from">
        <input  v-model="todo" class = "todo-input" type="text" placeholder="add a todo" />
        <div @click="add" class="todo-button">add todo</div>
   </div>

   <div v-for="(item,index) in list" :class="[item.isCompleted?'doed' :'item']">
    <div>
        <input v-model="item.isCompleted" type="checkbox">
        <span class="todoname">{{ item.text }}</span>
    </div>
    <span @click="del(index)" class="del">del</span>
   </div>

   <div class="div-tutton">
    <button class="mybutton">点我</button>
    <Mybutton  @ok="accept" text="你好"></Mybutton>
   <Mybutton text="大家好"></Mybutton>
   </div>
   
   

</div>
</template>

<style scoped>

    .top{
        width: 98%;
        margin: auto;
        height: 500px;
        background-color: #FFFF;
        border-radius: 5px;
        margin-top: 40px;
        padding-top: 15px;
        box-sizing: border-box; /*使用padding 造成数据变大可以使用这个*/
    }
    .text{
        margin-top: 30px;
        font-size: 28px;
        font-weight: 1000;
        text-align: center;
        
    }

    .todo-from{
      display: flex;
      margin-left: 30px;
      margin-top: 30px;

    
    }
    .todo-input{
        border: 1px solid #dfe1e5;
        outline: none;
        width: 70%;
        height: 50px;
        border-radius: 18px 0 0 18px;
        padding-left: 16px;
    }
    .todo-button{
        width: 80px;
        text-align: center;
        line-height: 50px;
        color:#FFFF;
        background: linear-gradient(to right, #7b2ff7, #2b9bf7); /* 紫色到蓝色渐变 */
        border-radius: 0 18px 18px 0;
        cursor: pointer;
        user-select: none;
    }

    .item{
        display: flex;
        width: 70%;
        height: 40px;
        align-items: center;
        justify-content: space-between; /* 水平方向平分空间 */
        border-radius: 20px;
        margin-top: 16px;
        margin-left: 60px;

        box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 20px;
       
    }
    .del{

        margin-right: 10px;
        color: red;
    }
    .doed{

      display: flex;
        width: 70%;
        height: 40px;
        align-items: center;
        justify-content: space-between; /* 水平方向平分空间 */
        border-radius: 20px;
        margin-top: 16px;
        margin-left: 60px;
        box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 20px;


        text-decoration: line-through;/*下划线*/
        opacity: 0.4;/*透明度*/

    }


    .mybutton{
      width: 100px;
      height: 50px;
      border-radius: 15px;
      margin-left: 15px;
      margin-top: 15px;
      background: linear-gradient(
    to right,
    rgb(113, 65, 168),
    rgba(44, 114, 251, 1)
  );
    }


    .div-tutton{
      display: flex;
    }
</style>
