<script setup>

const items=ref([]);
const text=ref();
function addtask(){
  if(items.value.includes(text.value))
  {
    alert("Task already present!")
  }
  else
  {
    items.value.push(text.value)
 
    text.value=""
  }
  
}
function arrayRemove(value) {
 
 items.value = items.value.filter(function (task) {
  console.log(task, value)
     return task !== value;
 })
}

function edit(value) {
  
  arrayRemove(value)
  text.value=value

}

  



</script>

<template>
  <title>
    To-Do List
  </title>
  <div class="bg-black min-h-screen text-white">
    <div class="flex justify-between w-full font-serif text-4xl py-4 pl-4 font-semibold bg-lime-800 " >      
        <div>
          Hey, e timpul să ne apucăm de treabă!
        </div>
        <div class="pr-5">
          😎
        </div>
    </div>
<div class="custom-shape-divider-top-1696606556">
    <svg data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1200 120" preserveAspectRatio="none">
        <path d="M321.39,56.44c58-10.79,114.16-30.13,172-41.86,82.39-16.72,168.19-17.73,250.45-.39C823.78,31,906.67,72,985.66,92.83c70.05,18.48,146.53,26.09,214.34,3V0H0V27.35A600.21,600.21,0,0,0,321.39,56.44Z" class="shape-fill"></path>
    </svg>
</div>
<div class="flex justify-center content-center py-5">
  <p class="text-3xl mr-10 py-3">
    Ce ai de făcut astăzi?  
   <form id="myform" @submit.prevent="addtask">
    <input v-model="text" placeholder="Ex: Spală mașina " size="40">
    <button class="ml-3 pl-6 pr-6 bg-lime-800 rounded m-3 " >
    Adaugă
   </button> 
  </form>
  </p>
</div>
<div class="h-5xl">
  <div class="flex box justify-center max-w-5xl m-auto text-stone-200">
    <ul  class="min-w-full border border-lime-800 rounded-lg " >
    <li v-for="item in items" class="text-2xl m-3" >
      <button @click ="arrayRemove(item)" class="rounded-full " >
        (✓)
      </button>
     
        {{item}}
        
      <button @click ="edit(item)" class="float-right">
         Edit
      </button> 
        
      
      
    </li>
  </ul>
  </div>
</div>
</div>
</template>
