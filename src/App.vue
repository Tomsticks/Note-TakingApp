

<template>
  <div v-if="toast" :class="clad"  class="toast ">
    <p>{{ content }}</p>
    <div v-if="determine" class="i">
    <i  class="fa-solid fa-check"></i>
  </div>
  </div>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.3.0/css/all.min.css" integrity="sha512-SzlrxWUlpfuzQ+pcUCosxcglQRNAq/DZjVsC0lE40xsADsfeQoEypE+enwcOiGjk/bSuGGKHEyjSoQ1zVisanQ==" crossorigin="anonymous" referrerpolicy="no-referrer"/>
  <link rel="stylesheet" href="../src/components/Tools/fontawesome-free-6.1.2-web/css/all.min.css">
    <nav>
<div class="head">
  <img src="../Images/b6e8918d522d99ae816a79676fc4e569.jpg" alt="">
  <h1>NOTE APP</h1>
</div>
<h3><i @click="openTextArea" class="fa-solid fa-book fa-2x"></i></h3>
<!-- <div class="add">
 <img src="../Images/boss_babby-removebg-preview (1).png" alt="">
</div> -->
</nav>
<div v-if="up" class="text">
  <!-- <img src="../Images/cute-cartoon-drawing-green-pen-digitally-generated-54023838-removebg-preview.png" alt=""> -->
  <div  class="text-con">
    <input v-model="head" type="text" placeholder="NOTE TITLE">
  <textarea v-model="text" name="add" id="" cols="30" rows="10"></textarea>
    <button @click="addNote">ADD</button>
</div>
</div>
<div class="notes-container">
  <div @click="sort" v-for="show in notes" :key="show.id" class="notes">
    <h1 >{{ show.title }}</h1>
      <p :contenteditable="choose"  class="note-book">{{ show.body, main }}</p>
  <div class="bottom">
    <p>{{ show.date.toLocaleString() }}</p>
    <p>{{ show.id }}</p>
    <div class="icons">
    <i @click="edit()" class="fa-solid fa-edit"></i> <br>
    <i @click="remove(show.id)" class="fa-solid fa-trash"></i>
  </div>
  </div>
  </div>
</div>
 <footer>
  <p>Made with 💖 by Miracle</p>
 </footer>
</template>

<script setup>
import {ref } from 'vue'

let notes = ref([])
let content = ref('You have succesfully Created a New note')
// function sort(id){
//   console.log(notes.id);

// }
// sort()
let head = ref('')
let text = ref('')
function addNote(){
  const newOnes ={
title: head.value,
body: text.value,
date: new Date(),
id: Math.floor(Math.random() * 50)
  }
    
  if(!head.value ){
    showTime() 
   
  }else{
    notes.value.push(newOnes)
head.value = ''
text.value = ' '
sucess()
  }
}
let determine = ref('true')
function sucess(){
    content.value = 'Sucessfuly added a new note✍✍'
    toast.value = true
    determine.value = true

}

let icon = ref(false)
function showTime(){
    content.value =  'Add Your Title 🤨📕📗'
    toast.value = true
    determine.value = false
    icon.value = true
}


let choose = ref(false)
let main = ref('hfgghj')

function edit(){
choose.value =!choose.value
}

function remove(id){
  console.log(id);
notes.value = notes.value.filter(item => {
  return item.id !== id
})

}
let up = ref(true)
function openTextArea(){
up.value = !up.value
}
let toast = ref(false)
function opentoast(){

  toast.value = true
}
</script>

<style scoped>

.toast{
 background: linear-gradient(to right, black, green);
  width: 50vh;
  padding: 20px ;
  color: white;
  box-shadow: 0 5px 6px 0 black;
  position: fixed;
  right:56vh;
  display: flex;
  overflow: hidden;
  transform: translateX(calc(100% + 30px));
  transition: all 0.5s cubic-bezier(0.68, -0.55, 0.25, 1.35);
  z-index: 10;
  font-size: 25px;
}

footer{
background-color: black;
color: white;
margin-top: 20vh;
padding: 10px;
box-shadow: 0 5px 7px 0 rgba(0, 0, 0, 0.89);
display: flex;
justify-content: center;
font-size: 20px;
width: 100%;
/* position: fixed; */
}

.toast .i{
  background-color: rgba(255, 255, 255, 0.171);
  width: 70px;
  height: 70px;
  display: flex;
  border-radius: 50%;
  align-items: center;
  justify-content: center;

}

</style>

