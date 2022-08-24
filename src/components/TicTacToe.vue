<template>
<div>
<div class='logo'></div>
  <div class="colorP1 skinSelect">
    <p class='marginPlayer'>Player 1</p>
    <div class='flex'>
      <SkinSelector :name="skin" v-bind:id='"selectSkinP1" + index' v-for="(skin, index) of skins" :key="index" @click="Selectskin(index,0)">
      </SkinSelector>
    </div>
  </div>
  <div class="colorP2 skinSelect">
    <p class='marginPlayer'>Player 2</p>
    <div class='flex'>
      <SkinSelector :name="skin" v-bind:id='"selectSkinP2" + index' v-for="(skin, index) of skins" :key="index" @click="Selectskin(index,1)">
      </SkinSelector>
    </div>
  </div>
  <input type='button' class='startButton' value='START'/>
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
    skins: ['\u2717','\u2B58','\u2605', "\u269C", "\u2660", "\u2665", "\u2663", "\u2666"],
    playerSkin: ['\u2717','\u2B58'],
  }
 },
 methods: {
    Selectskin (index,player){
      this.playerSkin[player] = this.skins[index];
      let skinButton
      let i = 0;
      this.skins.forEach(skin => {
        skinButton = document.getElementById("selectSkinP"+ (player + 1) + i);
        if(this.playerSkin[player] == skin){
          skinButton.style.backgroundColor = 'grey';
        }else{
          skinButton.style.backgroundColor = 'white';
        }
        i++
      });
    },
  }
}

/*let xhr = new XMLHttpRequest();
xhr.onreadystatechange = () => {
  if(xhr.readyState === 4 && xhr.status === 200)
  {
    console.log(JSON.parse(xhr.response));
  }
};
xhr.open('GET', 'https://api.github.com/users/KuribOP');
xhr.send(null);*/
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
  justify-content:center;
}
.logo {
  background-image:url(../assets/logo.png);
  background-size:100% 100%;
  height:20vh;
  width:auto;
  align:center;
}
.marginPlayer {
  margin-top:0;
}

.startButton{
  font-size:10vh;
}
</style>
