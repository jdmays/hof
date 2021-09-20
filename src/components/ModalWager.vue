<template>
    <div class="modal border-2 w-1/4 border-indigo-200 rounded-lg rounded shadow-lg z-50 "> 


    <div class="flex items-center pb-3">
      <p class="text-1xl font-bold">Select your Racer and Enter Your Wager:</p>
    </div>

    <div class="flex justify-center items-center max-w-sm">

   <form class="bg-white rounded px-8 pt-6 pb-8 mb-4" @submit="handleSubmit">


    <div class="mb-4">
      <select v-model="dogId" ref="dogId" class="w-full h-10 pl-3 pr-6 text-base text-gray-900 placeholder-gray-600 border border-gray-300 rounded-lg appearance-none focus:shadow-outline" 
      placeholder="Select">
      <option value="0">--Select--</option>
      <option value="1">Seabiscuit</option>
      <option value="2">Native Dancer</option>
      <option value="3">Bust-a-Move</option>
      <option value="4">Doctor Strange</option>
      <option value="5">Zenyatta</option>
      <option value="6">Tabasco Cat</option>
      </select>
      <span v-if="errmsg.dogId">{{errmsg.dogId}}</span>
    </div>

    <div class="absolute inset-y-0 right-0 flex items-center px-2 pointer-events-none">
      <svg class="w-4 h-4 fill-current" viewBox="0 0 20 20">
      <path 
      d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd" fill-rule="evenodd">
      </path>
      </svg>
    </div>

    <div class="relative flex-1">
      <input id="wageramt" 
      name="wageramt" 
      ref="wagerAmt" 
      type="number" 
      v-model="wagerAmt" 
      class="peer h-10 w-full border border-1.5 rounded-md focus:shadow-outline
      border-gray-300 text-gray-900 placeholder-transparent focus:outline-none focus:border-blue-600 focus:border-2 p-3" placeholder="quelquechose" />
      <span v-if="errmsg.wagerAmt">{{errmsg.wagerAmt}}</span>
      <label for="eta" class="absolute left-2 px-1 -top-2.5 bg-white 
      text-blue-600 text-sm transition-all peer-placeholder-shown:text-base 
      peer-placeholder-shown:text-gray-900 peer-placeholder-shown:top-2 
      peer-focus:-top-2.5 peer-focus:text-red-600 
      peer-focus:text-sm">Wager Amount:</label>

      <div class="absolute right-0 top-0 mt-2 mr-2">
      <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-blue-600" fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 8c-1.657 0-3 .895-3 2s1.343 2 3 2 3 .895 3 2-1.343 2-3 2m0-8c1.11 0 2.08.402 2.599 1M12 8V7m0 1v8m0 0v1m0-1c-1.11 0-2.08-.402-2.599-1M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
      </svg>
      </div>

      </div>

    <div class="flex items-center justify-between pt-10">
      <button @click="handleSubmit" class="bg-blue-600 hover:bg-blue-200 hover:text-blue-600 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="submit">
      Place Bet
      </button>
      <button @click="closeWager" class="bg-blue-200 hover:bg-blue-600 hover:text-white text-blue-600 font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="button">
      Cancel
      </button>
    </div>

</form>
    </div>

    </div>
</template>

<script>
export default {
  name: 'modalwager',
  data() {
    return {
    dogId: 0,
    wagerAmt: 0,
    errmsg: []
    }
  },
    methods: {
       closeWager() {
            this.$emit('closeWager')
        },
        cancelWager() {
            this.$emit('cancelWager')
        },
        getWagerAmt() {
            this.$emit('wagerAmt')
        },
        handleSubmit() {

        localStorage.setItem('dogId',this.dogId)
        localStorage.setItem('wagerAmt',this.wagerAmt)

        this.closeWager();
        },
        checkWager() {
          // make sure they have enough money.
        }
    },
    mounted() {
      // get the account amount
      this.$refs.wagerAmt.value = '';
      this.$refs.dogId.focus();
    }
    
}
</script>

<style>
.dropdown:hover .dropdown-menu {
  display: block;
}
</style>