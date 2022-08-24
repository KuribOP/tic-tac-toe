<template>
<div>
<h1>TIC-TAC-TOE</h1>
<div class="colorP1 , skinSelect">
  <p>Player 1</p>
  <div class='flex'>
    <SkinSelector :name="skin" v-for="(skin, index) of skins" :key="index" @click="Selectskin(1)">
    </SkinSelector>
  </div>
</div>

</div>
</template>

<script>
import SkinSelector from './SkinSelector.vue'
export default {
  name: 'TicTacToe',
  components: {
    SkinSelector
  },
 data() {
  return {
    skins: ['\u2605', "blue"],
    playerSkin: ['dzs','sfe'],
    item: '',
  }
 },
 methods: {
    Selectskin (player){
       this.playerSkin[player] = this.skin;
       console.log(this.item);
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.colorP1{
  background-color:red;
}
.colorP2{
  background-color:blue;
}
.skinSelect{
  width:100%;
  height:auto;
}
.flex {
        display:flex;
        flex-wrap:wrap;
        }
</style>
