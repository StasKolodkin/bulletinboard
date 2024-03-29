<template>
    <div class="forSaleWindow">
        <div class="forSaleWrapper">
            <div class="titleForSale">
                <span>МОИ ОБЪЯВЛЕНИЯ</span>
            </div>
            <div class="forSaleLots">
                <div class="listLots">
                    <div class="gridLots">
                        <div v-for="lot in lots" :key="lot.index" class="blockLot">
                            <div class="wrapperLot">
                                <div class="leftSubBlock">
                                    <div class="imgLot">
                                        <!-- <img :src="getImagePath(lot[1])"> -->
                                        <img :src="getImagePathChild(lot[6])">
                                    </div>
                                    <div class="DownLeftSubBlock">
                                        <span class="nameLot">{{ lot[1] }}</span>
                                    <div class="priceLot">
                                        <span class="priceTextLot">Цена: </span>
                                        <span class="priceSumLot">{{ lot[2] }}</span>
                                    </div>
                                    </div>
                                </div>
                                <div class="rightSubBlock">
                                    <div class="UpRightSubBlock">
                                        <div class="timerLot">
                                            <img src="./assets/svg/timing.svg">
                                            <span>{{ lot[3] }}</span>
                                        </div>
                                        <div class="addItems">
                                            <div v-for="(imageName, imgIndex) in lot[4]" :key="imgIndex" class="addItem">
                                                <img :src="getImagePathChild(imageName)">
                                            </div>
                                        </div>
                                    </div>
                                    <div class="DownRightSubBlock">
                                        <div class="DownRightButton" @click="openModalPrice(lot[0])">
                                            <button type="reset" class="buttonLot">
                                                <span class="buttonLotText">изменить</span>
                                            </button>
                                        </div>
                                        <ModalPrice :isVisiblePrice="modalPrice" :id="pickedId" @closeModalPrice="handleClosePrice"></ModalPrice>
                                        <div class="DownRightButton" @click="sendRemoveConfirmation(lot[0])">
                                            <button type="reset" class="buttonLot">
                                                <span class="buttonLotText">снять</span>
                                            </button>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <!-- <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div>
                        <div class="blockLot"></div> -->
                    </div>
                </div>
            </div>
            <div class="forSaleBackButton" @click="resetMainWindow">
                <button type="reset" class="buttonReset">
                    <span class="buttonResetText">назад</span>
                </button>
            </div>
        </div>
    </div>
</template>

<style>
    @import './style/forSaleWindow.css';
    @import './style/mainWindow.css';
    @import './style/sellWindow.css';
</style>

<script>
    import { searchScript } from './scripts/searchScript';
    import ModalPrice from '@/components/ModalPrice.vue'
   
    export default {
        ...searchScript,
        components: {
            ModalPrice,
        },

    methods: {

        ...searchScript.methods, 

    resetMainWindow() {
        this.$emit('toggleViewSale'); 
    },
    },
    }
</script>