<template>
  <div v-if="isVisibleContent" class="mainWindow">
  <div class="forButton">
    <button class="closeMain" @click="closeMainWindow">
    <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 14 14" fill="none">
      <path d="M1.4 14L0 12.6L5.6 7L0 1.4L1.4 0L7 5.6L12.6 0L14 1.4L8.4 7L14 12.6L12.6 14L7 8.4L1.4 14Z"/>
    </svg>
    </button>
    </div>
    <div class="allAssets">
      <div class="firstCircle"></div>
      <div class="firstAsset">
        <img src="./assets/png/paperOne.png">
      </div>
      <div class="secondAsset">
        <img src="./assets/png/paperTwo.png">
      </div>
      <div class="thirdAsset">
        <img src="./assets/png/paperThree.png">
      </div>
      <div class="fourthAsset">
        <img src="./assets/png/paperFour.png">
      </div>
      <div class="secondCircle"></div>
    </div>
    
    <BulletinBoard></BulletinBoard>
  </div>
</template>

<style>
  @import './style/mainWindow.css';
</style>

<script>
  import { searchScript } from './scripts/searchScript.js';
  import BulletinBoard from '@/components/BulletinBoard.vue';

  export default {
  data() {
    return {
      
      ...searchScript.data(),
    };
  },
  components: {
    BulletinBoard,
  },
  methods: {
    ...searchScript.methods,
},

mounted() {
    this.fetchDataFromBackend();
    //window.addEventListener('keypress', (e) => {this.closeMainWindow(e)})

    window.events.addEvent('visibleStatus', (status) => {
      this.handleKeydown(status)
    });
  }
}
</script>
