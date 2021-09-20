<template>
  
<div class="overflow-hidden relative flex items-center min-h-screen">
  <div class="absolute top-0" style="border-bottom-left-radius: 50% 20%; border-bottom-right-radius: 50% 20%;"></div>
  <div class="absolute inset-x-auto w-full z-10">
    <div class="w-3/4 mx-auto shadow-md rounded-md p-4 bg-white">

      <div class="flex gap-2 flex-col md:flex-row center">
        <div class="relative flex-1">
          <input id="acctAmt" name="acctAmt" v-model="acctAmt" type="text" class="peer h-10 w-full border border-1.5 rounded-md border-gray-300 text-gray-900 placeholder-transparent focus:outline-none focus:border-red-600 focus:border-2 p-3" placeholder="balance" />
          <label for="acctAmt" class="absolute left-2 px-1 -top-2.5 bg-white text-red-600 text-sm transition-all peer-placeholder-shown:text-base peer-placeholder-shown:text-gray-900 peer-placeholder-shown:top-2 peer-focus:-top-2.5 peer-focus:text-red-600 peer-focus:text-sm">
        Account Balance:
        </label>
        </div>

        <div class="relative flex-1">
          <input  type="text" class="peer h-10 w-full border border-1.5 rounded-md border-gray-300 text-gray-900 placeholder-transparent focus:outline-none focus:border-red-600 focus:border-2 p-3" placeholder="quelquechose" />
          <label for="arrival" class="absolute left-2 px-1 -top-2.5 bg-white text-red-600 text-sm transition-all peer-placeholder-shown:text-base peer-placeholder-shown:text-gray-900 peer-placeholder-shown:top-2 peer-focus:-top-2.5 peer-focus:text-red-600 peer-focus:text-sm">Dachshund 1:</label>
        </div>

        <div class="relative flex-1">
          <input id="wageramt" name="wageramt" type="text" v-model="wagerAmt"
          class="peer h-10 w-full border border-1.5 rounded-md 
          border-gray-300 text-gray-900 placeholder-transparent focus:outline-none focus:border-red-600 focus:border-2 p-3" placeholder="quelquechose" />
          <label for="eta" class="absolute left-2 px-1 -top-2.5 bg-white 
          text-red-600 text-sm transition-all peer-placeholder-shown:text-base 
          peer-placeholder-shown:text-gray-900 peer-placeholder-shown:top-2 
          peer-focus:-top-2.5 peer-focus:text-red-600 
          peer-focus:text-sm">Wager Amount:</label>
          <div class="absolute right-0 top-0 mt-2 mr-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-red-600" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
            </svg>
          
          </div>
        </div>
        <div class="relative flex-1">
          <input id="etd" name="etd" type="text" 
          class="peer h-10 w-full border border-1.5 rounded-md border-gray-300 text-gray-900 
          placeholder-transparent 
          focus:outline-none 
          focus:border-red-600 focus:border-2 p-3" 
          placeholder="quelquechose" />

          <label for="etd" 
          class="absolute left-2 px-1 -top-2.5 bg-white 
          text-red-600 text-sm transition-all peer-placeholder-shown:text-base 
          peer-placeholder-shown:text-gray-900 peer-placeholder-shown:top-2 
          peer-focus:-top-2.5 peer-focus:text-red-600 peer-focus:text-sm">Dachshund 2:</label>
        </div>
    
        <div class="relative flex-1">
          
          <input id="etd" name="etd" type="text" 
          class="peer h-10 w-full border border-1.5 rounded-md border-gray-300 text-gray-900 
          placeholder-transparent 
          focus:outline-none 
          focus:border-red-600 focus:border-2 p-3" 
          placeholder="quelquechose" />

          <label for="etd" 
          class="absolute left-2 px-1 -top-2.5 bg-white 
          text-red-600 text-sm transition-all peer-placeholder-shown:text-base 
          peer-placeholder-shown:text-gray-900 peer-placeholder-shown:top-2 
          peer-focus:-top-2.5 peer-focus:text-red-600 peer-focus:text-sm">Wager Amount 2:</label>
          <div class="absolute right-0 top-0 mt-2 mr-2">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-red-600" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
            </svg>
          </div>
        </div>
   
      </div>

      <div class="flex justify-center mt-6">
        <button class="bg-red-900 text-white font-extrabold text-lg rounded-full px-6 py-3">Start Race</button>
      </div>
    
    </div>
  </div>
</div>


  
        <div class="flex justify-items-start">
          Your Account Balance: ${{ acctAmt }}

        <form @submit.prevent="handleSubmit">
        <label class="pr-1">Wager Amount:</label>
        <input class="pl-1" type="text" name="wageramt" id="wageramt" >
        <button class="bg-blue-600 hover:bg-blue-200 text-white hover:text-blue-600 py-2 font-bold px-4 rounded-lg">Place Bet</button>
        </form>

        </div>

<!--
        <label>Wager on Which Dachshund?</label>
        <select w-full border bg-white rounded px-3 py-2 outline-none v-model="whichDach">
        <option class="py-1" value="1">name1</option>
        <option class="py-1" value="2">name2</option>
        <option class="py-1" value="3">name3</option>
        <option class="py-1" value="4">name4</option>
        </select> -->




</template>

<script>
export default {
data() {
  return {
    wagerAmt: 0,
    acctAmt: 10000
  }
},
mounted() {
   this.wagerAmt = localStorage.wagerAmt;
   localStorage.setItem('acctAmt',this.acctAmt);
} ,
methods: {
  checkBalance() {

  },
  wagerAmount() {
   // localStorage.setItem('wagerAmt', this.wagerAmt);
  },
  adjustAccount() {

  },
  handleSubmit() {
    console.log('wager amount',this.wagerAmt)
    localStorage.setItem('wagerAmt',this.wagerAmt);
  }
}
}
</script>

<style>

</style>