<template>

<!-- shows the current account balance. I thought they might miss it if it was up in the header -->
<div class="flex justify-center items-center" v-if="!showModalWager && !readyToRace">
    <span class="text-blue-600 font-bold py-2">Account Balance: ${{ acctAmt }}</span>
</div>

<!-- a convenient place to say, hey, it's over pal. -->
<div class="justify-center items-center" v-if="noMorePlay">
    <span class="text-blue-600 font-bold py-2">Sadly, you've lost.  It's Over. </span>
    <p> <button @click="resetAll" class="bg-blue-600 
    hover:bg-blue-200 text-white hover:text-blue-600 py-2 font-bold px-4 rounded-lg">Play Again</button></p>
</div>
<!-- they have to do this before anything else -->
<div v-if="!showModalStart && !readyToRace && !showModalWager && !noMorePlay">
    <button @click="toggleModalWager" class="bg-blue-600 
    hover:bg-blue-200 text-white hover:text-blue-600 py-2 font-bold px-4 rounded-lg">Place Your Bet to Start</button>
</div>
<!-- triggers the race -->
<div v-if="readyToRace && !raceOver">
    <button @click="runDogs" :disabled="isDisabled" 
    class="bg-blue-600 disabled:opacity-50 hover:bg-blue-200 text-white hover:text-blue-600 py-2 font-bold px-4 rounded-lg">
    Start Race</button>
</div>

<!-- ok, i admit it. this whole modal should be its own component.  
But... cant seem to emit the required stuff back from it. -->
<div v-if="showModalWager">
<form ref="wagerForm" id="wagerForm">
<div class="modal border-2 w-2/5 border-indigo-200 rounded-lg rounded shadow-lg z-50 "> 

<div class="flex justify-center items-center">
    <p class="text-1xl font-bold">Select your Racer and Enter Your Wager:</p>
</div>

<div class="flex justify-center items-center">
<div class="bg-white rounded pt-10 pb-2 mb-4">

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
     <span class="text-red-600 font-bold" v-if="errmsg.dogId">{{errmsg.dogId}}</span>
</div>

<div class="absolute inset-y-0 right-0 flex items-center px-2 pointer-events-none">
    <svg class="w-4 h-4 fill-current" viewBox="0 0 20 20">
    <path 
    d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd" fill-rule="evenodd">
    </path>
    </svg>
</div>

<div class="relative flex-1">
    <input id="wageramt" name="wageramt" ref="wagerAmt" type="text" v-model="wagerAmt" class="peer h-10 w-full border border-1.5 rounded-md focus:shadow-outline
border-gray-300 text-gray-900 placeholder-transparent focus:outline-none focus:border-blue-600 focus:border-2 p-3" placeholder="quelquechose" />
 <span class="text-red-600 font-bold" v-if="errmsg.wagerAmt">{{errmsg.wagerAmt}}</span>
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
    <button @click="closeWager" class="bg-blue-600 hover:bg-blue-200 hover:text-blue-600 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="submit">
    Place Bet
    </button>
    <button @click="cancelWager" class="bg-blue-200 hover:bg-blue-600 hover:text-white text-blue-600 font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="button">
    Cancel
    </button>
</div>


</div>

</div>

</div>
</form>
<!-- end if modal wager -->
</div>


<div class="top-0 p-2 mx-auto">
     <div v-if="showModalStart">
        <Modal @closeModal="toggleModalStart"/>
    </div>
    <div v-if="raceOver">
        <ModalResult @playAgain="playAgain" @stopPlaying="stopPlaying" :msg="msg" :resultMsg="resultMsg" :commentMsg="commentMsg" :resultActions="resultActions" :acctAmt="acctAmt"/>
    </div>
  <div v-if="!showModalStart && !showModalWager && !raceOver">


   <main role="main" ref="racetrack" class="w-full px-2 space-y-0">
<!-- these are static not dynamic as I originally intended.  Could not get dynamically assigned images to show -->
            <div class="text-left py-0 dogz" id="dog1" dog2_id="dog1_id">
            <img class="transform scale-75" src="@/assets/dachs1.png" /> 
            <span class="pl-8">{{dogNames[0]}}</span>
            </div>

            <div class="text-left py-0 dogz" id="dog2" dog2_id="dog2_id">
            <img class="transform scale-75" src="../assets/dachs2.png" alt="">
            <span class="pl-8">{{dogNames[1]}}</span>
            </div>

            <div class="text-left py-0 dogz" id="dog3" doc3_id="dog3_id">
            <img class="transform scale-75" src="../assets/dachs3.png" alt="">
            <span class="pl-8">{{dogNames[2]}}</span>
            </div>

            <div class="text-left dogz" id="dog4" dog4_id="dog4_id">
            <img class="transform scale-75" src="../assets/dachs4.png" alt="">
            <span class="pl-8">{{dogNames[3]}}</span>
            </div>

            <div class="text-left dogz" id="dog5" dog4_id="dog5_id">
            <img class="transform scale-75" src="../assets/dachs5.png" alt="">
            <span class="pl-8">{{dogNames[4]}}</span>
            </div>

            <div class="text-left py-0 dogz" id="dog6" dog6_id="dog6_id">
            <img class="transform scale-75" src="../assets/dachs6.png" alt="">
            <span class="pl-8">{{dogNames[5]}}</span>
            </div>

        </main>


        </div>
        </div>

</template>

<script>
import Footer from './Footer.vue';
import Dog from './Dog.vue';
import dogsData from "../data/dogs.json";
import congratsData from "../data/congrats.json";
import consolesData from "../data/consoles.json";

import Account from './Account.vue';
import Modal from './Modal.vue';
import ModalResult from './ModalResult.vue';

//import ModalWager from './ModalWager.vue'
import DogBio from './DogBio.vue';

import { gsap } from "gsap"

export default {
name: 'Track',
components: {
    Footer, Dog, Account, Modal, ModalResult, DogBio
},
data() {
    return {
        dogsData: null, // the orignal data from the json file.  not being used but left fyi
        congratsData: null, // A little sentence that they see randomly after each race
        dogSpeed: [1,2,3,4,5,6], // this determines who will win
        winnerId: 0, // the winner
        windowWidth: 0, // to keep the dogs from running off the end of the page
        dogId: 0, // the dog chosen
        numRaces: 0, // originally used in order to be able to reduce the randomness of the races
        dogName: null, 
        showModalStart: true, //the very first modal when the app is opened
        showResult: false,
        showModalWager: false,
        acctAmt: 10000,
        wagerAmt: null,
        totalAcct: 0,
        isDisabled: true,
        showDogBio: false,
        raceOver: false,
        msg: null,
        resultMsg: null,
        commentMsg: null,
        resultActions: null,
        readyToRace: false,
        wagerAmtIsBad: false,
        noMorePlay: false,
        errmsg: [],
        dogNames: ['Seabiscuit','Native Dancer','Bust-a-Move','Doctor Strange','Zenyatta','Tabasco Cat','War Emblem','Jack','Lexie']
    }
},
methods: {
        /* closes the wager modal after betting has taken place */
        closeWager() {
            this.acctAmt  = localStorage.getItem('acctAmt');
            this.showModalWager = false;
            this.readyToRace = true;
            let wa = this.wagerAmt;
            wa = parseInt(wa);
            this.wagerAmt = wa;
            
            localStorage.setItem('wagerAmt',this.wagerAmt);
            localStorage.setItem('dogId',this.dogId);
        
        },
        /* lets them do it again */
        playAgain() {
            this.raceOver = false;
            this.readyToRace = false;
            if (this.acctAmt < 1) {
            this.noMorePlay = true;
            } else {
            this.noMorePlay = false;
            }
        },
        /* basically like quit */
        stopPlaying() {
            this.raceOver = false;
            this.readyToRace = false;
            this.showModalStart = true;
            this.wagerAmt = 0;
            this.acctAmt = 0;
            this.dogId = 0;
        },
        resetAll() {
            this.wagerAmt = 0;
            this.acctAmt = 10000;
            this.noMorePlay = false;
            localStorage.setItem('wagerAmt',0);
            localStorage.setItem('dogId',0);

            this.showModalStart = !this.showModalStart
        },
        cancelWager() {
            this.showModalWager = !this.showModalWager;
            this.readytoRace = false;
        },  
        toggleDogBio() {
            this.showDogBio = !this.showDogBio
        },
        toggleModalStart() {
            this.showModalStart = !this.showModalStart
            },
        toggleModalWager() {
            this.resetDogs()
            this.showModalWager = !this.showModalWager
            this.isDisabled = false
            // i have no idea why this doesn't work. :(
           // this.$refs.dogId = 0;
           // this.$refs.wagerAmt.value = "";
            },
       getWindowWidth() {
           this.windowWidth = this.$refs.racetrack.clientWidth - 175
            },
         /* starts the race */   
       runDogs() {
           // shuffles the dogSpeed array to get the next winner
           this.shuffle(this.dogSpeed)
           this.getWindowWidth();
           // would've established a cycle to mess with the randomness
           this.numRaces++;
           if( this.numRaces > 6) {
            this.numRaces = 1;
           }
           // stores the race number
           localStorage.setItem('numRaces',this.numRaces)

            if (this.numRaces == 1) {
            this.dogId = localStorage.getItem('dogId');
            }

        this.determineWinner(this.dogSpeed)
        gsap.to("#dog1", {x: this.windowWidth, duration: this.dogSpeed[0]});
        gsap.to('#dog2', {x: this.windowWidth, duration: this.dogSpeed[1]})
        gsap.to('#dog3', {x: this.windowWidth, duration: this.dogSpeed[2]})
        gsap.to('#dog4', {x: this.windowWidth, duration: this.dogSpeed[3]})
        gsap.to('#dog5', {x: this.windowWidth, duration: this.dogSpeed[4]})
        gsap.to('#dog6', {x: this.windowWidth, duration: this.dogSpeed[5]})  
        // to prevent the rather jarring transition after the game is over.    
        setTimeout(() => {  this.raceOver = true }, 6000);
       },
        resetDogs() {
        localStorage.setItem('dogId',0)
        localStorage.setItem('wagerAmt',0)
        localStorage.setItem('winnerId',0)
       
        gsap.to('#dog1', {rotation: 360,x: 0, duration: 1})
        gsap.to('#dog2', {rotation: 360,x: 0, duration: 1})
        gsap.to('#dog3', {rotation: 360,x: 0, duration: 1})
        gsap.to('#dog4', {rotation: 360,rotation: 360, x: 0, duration: 0.6})
        gsap.to('#dog5', {rotation: 360,x: 0, duration: 1})
        gsap.to('#dog6', {rotation: 360,x: 0, duration: 1})
       },
       shuffle(arr) {
        let m = arr.length;
            while (m) {
                const i = Math.floor(Math.random() * m--);
                [arr[m], arr[i]] = [arr[i], arr[m]];
            }
                this.numRaces  = localStorage.getItem('numRaces');
                this.dogId  = localStorage.getItem('dogId');
                this.winnerId=arr.indexOf(Math.min.apply(null,arr)) + 1
                this.dogSpeed = arr;
        },
       determineWinner(arr) {
        this.winnerId=arr.indexOf(Math.min.apply(null,arr)) + 1      
        this.dogId  = localStorage.getItem('dogId');
        this.msg = this.dogNames[this.winnerId] + " is the Winner!"

        if (this.winnerId == this.dogId) {   
        this.resultMsg = "You wagered correctly!"
        this.totalAcct = Number(this.acctAmt) + Number(this.wagerAmt);
        this.commentMsg = congratsData[Math.floor(Math.random() * 10)];
        this.acctAmt = this.totalAcct;
        localStorage.setItem('acctAmt',this.acctAmt)
        localStorage.setItem('wagerAmt',0)
       } else {
        this.totalAcct = Number(this.acctAmt) - Number(this.wagerAmt);
        this.acctAmt = this.totalAcct;
        localStorage.setItem('acctAmt',this.acctAmt)
        this.resultMsg = "You lost."
        this.commentMsg = consolesData[Math.floor(Math.random() * 10)];
        localStorage.setItem('wagerAmt',0)
       }

       },
       validateWagerAmt(value) {
           if(value > this.acctAmt){
               this.errmsg['wagerAmt'] = "You cannot bet more than you have!";
               this.showModalWager = true;
               this.readyToRace = false;
           } else {
               this.errmsg['wagerAmt'] = '';
           }
       },
       validateDogId(value) {
            if( value < 1 || value > 6) {
                this.errmsg['dogId'] = "Select A Hound";
                this.showModalWager = true;
                this.readyToRace = false;
            } else {
                this.errmsg['dogId'] = '';
            }
       }  
},
watch: {
    wagerAmt(value) {
        this.wagerAmt = value;
        this.validateWagerAmt(value);
    },
    dogId(value) {
        this.dogId = value;
        this.validateDogId(value);
    }
},
mounted() {
    this.congratsData = congratsData;
    this.consolesData = consolesData;
    localStorage.setItem('dogId',0)
    localStorage.setItem('wagerAmt',0)
    localStorage.setItem('winnerId',0)
    //this.dogsData = dogsData;
    localStorage.setItem('acctAmt',this.acctAmt);

}

}
</script>

<style>


</style>