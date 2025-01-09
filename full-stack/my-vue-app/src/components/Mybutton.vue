<script setup>
import { defineProps } from 'vue';
import { defineEmits } from 'vue';

const props = defineProps(['text'])
const emit = defineEmits(['ok'])

function send(){
    emit('ok','hello')
}

</script>
<template>
    <div>
    <button @click="send" class="mybutton">{{ props.text }}</button>
   </div>
</template>
<style>
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
</style>