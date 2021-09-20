<template>
     <div class="modal border-2 w-3/5 border-indigo-200 rounded-lg rounded shadow-lg z-50 "> 


        <div class="flex items-center pb-3">
          <p class="text-1xl font-bold">The World Weiner Dog Racing League Presents:</p>
        </div>
        <div class="flex justify-center items-center pb-3">
          <p class="text-6xl font-bold">Hounds of Fury</p>
        </div>
                <!--Body-->
        <div class="space-y-5">
        <div class="flex justify-center">
        <p class="text-left text-2xl">Become fabulously rich by betting on racing weiner dogs.</p> 
        </div>

        <div class="flex justify-center space-y-4">
        <p class="text-left text-2xl">To play, select the fastest hound, wager an amount, and Race!</p>
        </div>


        <div class="flex justify-center pt-8">
          <button @click="closeModal" class="px-4 bg-blue-600 p-3 rounded-lg text-white font-bold hover:bg-blue-200 hover:text-blue-600 mr-2">Let's Play</button>

        </div>
  
        </div>


    </div>
</template>

<script>
export default {
    data() {
        return {
            something: 0
        }
    },
    methods: {
        closeModal() {
            this.$emit('closeModal')
        }
    }
}
</script>




<style>

.modal {
    width: 1000px;
    height: 400px;
    padding: 20px;
    margin: 100px auto;
    background: white;
    border-radius: 10px;
}
.backdrop {
    top: 0;
    position: fixed;
    background: rgba(0,0,0,0.5);
    width: 100%;
    height: 100%;
}

.modal.sale h1 {
    color: white;
}
.modal.sale .actions {
    color: white;
}
.modal .actions a {
    color: #333;
    padding: 8px;
    border: 1px solid #eee;
    border-radius: 4px;
    text-decoration: none;
    margin: 10px;
}

</style>