<template>
  <div v-if="isVisible">
      <div class="modalOverlay" @click="closeModal"></div>
      <div class="modalWindow">
      <div class="modalWrapper">
          <div class="modalTittle">
              <span>вы уверены?</span>
          </div>
          <div class="modalText">
              <span>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</span>
          </div>
          <div class="modalImg">
              <img :src="image">
          </div>
          <div class="modalButtonBlock">
              <!-- <button class="modalButton" @click="sendPurchaseConfirmation"> -->
              <button class="modalButton" @click="test">
              <span class="modalButtonText">Я уверен в покупке</span>
              </button>
          </div>
      </div>
      </div>
  </div>
  </template>
  
  <script>
  import { searchScript } from './scripts/searchScript.js';
  
  export default {
    ...searchScript,
    props: {
      isVisible: Boolean,
      image: String,
      id: String,
    },
    methods: {
      ...searchScript.methods,

      test(){
        //executeClient('sendPurchaseConfirmation', JSON.stringify(purchaseData));
        //console.log(`test: ${searchScript.data().selectedId}`)
        window.events.callEvent('sendPurchaseConfirmation')
        this.closeModal();
      }
    }
  };
  </script>
  
  <style>
    @import './style/modalWindow.css';
  </style>
  