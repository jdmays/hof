<template>
<nav class="bg-gray-100">

<div class="max-w-6xl mx-auto">
<div class="flex justify-between">
<div class="flex space-x-1">
<div>
    <a target="_new" href="https://www.jdmays.com" class="flex items-center py-5 px-1 text-gray-700">

<svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-yellow-600" viewBox="0 0 512 512">
<path d="M304 384v-24c0-29 31.54-56.43 52-76 28.84-27.57 44-64.61 44-108 0-80-63.73-144-144-144a143.6 143.6 0 00-144 144c0 41.84 15.81 81.39 44 108 20.35 19.21 52 46.7 52 76v24M224 480h64M208 432h96M256 384V256" fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="32"/><path d="M294 240s-21.51 16-38 16-38-16-38-16" fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="32"/>
</svg>
 <span class="font-bold text-blue-600">Jim Labs</span>
    </a>
<!-- end logo -->
</div>

</div>


<div class="hidden md:flex items-center space-x-1 px-3">

<button @click="triggerTime" class="py-2 px-3 bg-yellow-400 text-blue-600 hover:bg-yellow-200 hover:text-red-900 rounded transition duration-300">

<svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
</svg>

</button>
<!-- end secondary nav -->
</div>

<!-- mobile nav -->

<div class="md:hidden flex items-center"> 
    <button>
<svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" viewBox="0 0 20 20" fill="currentColor">
  <path fill-rule="evenodd" d="M3 5a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 10a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1zM3 15a1 1 0 011-1h12a1 1 0 110 2H4a1 1 0 01-1-1z" clip-rule="evenodd" />
</svg>
</button>
<!-- end mobile nav -->
</div>
</div>
<!-- mobile menu -->
<div class="hidden md:hidden">

<!-- end mobile menu -->
</div>
</div>


     <div v-if="showTime" class="modal border-2 w-3/5 border-indigo-200 rounded-lg rounded shadow-lg z-50 "> 


        <div class="flex justify-center items-center pb-3">
          <p class="text-4xl font-bold">Information</p>
        </div>

        <div class="space-y-5">
        <p class="flex justify-center text-left text-1xl">I'll put more in-depth information in a ReadMe file.</p>
        <p class="flex justify-center text-left text-1xl pb-5"> For now, this is how my 
            time breaks down in the completion of this exercise:</p>
        </div>

        <div class="flex pl-8 justify-center">
        <ul class="divide-y divide-gray-100 list-disc">
        <li class="p-1 hover:bg-blue-600 hover:text-blue-200 text-left">
         Friday, 9/17:  Determine game concept and basic layout - 2 hrs.
        </li>
        <li class="p-1 hover:bg-blue-600 hover:text-blue-200 text-left">
        Saturday, 9/18:  Game Play including Animation - 4 hrs.
        </li>
        <li class="p-1 hover:bg-blue-600 hover:text-blue-200 text-left">
        Monday, 9/20: Revise sequence of Modals, check for edge cases, add validation - 3hrs.
        </li>
    </ul>
    </div>


        <div class="flex justify-center pt-8">
          <button @click="triggerTime" 
          class="px-4 bg-blue-600 
          p-3 rounded-lg text-white font-bold hover:bg-blue-200 hover:text-blue-600 mr-2">
          <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 14l2-2m0 0l2-2m-2 2l-2-2m2 2l2 2m7-2a9 9 0 11-18 0 9 9 0 0118 0z" />
            </svg>
          </button>

  
        </div>


    </div>





</nav>


</template>

<script>
export default {
name: 'navbar',
data() {
    return {
        acctAmt: 10000,
        showTime: false
    }
},
methods: {
    triggerTime() {
        this.showTime = !this.showTime;
    }
},
mounted() {

}
}
</script>

<style>

</style>