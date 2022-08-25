<template>
  <div id='titleScreen'>
    <div class='logo'></div>
    <div class="colorP1 skinSelect">
      <p class='marginPlayer'>Player 1</p>
      <div class='flex wrap'>
        <SkinSelector :name="skin" v-bind:id='"selectSkinP1" + index' v-for="(skin, index) of skins" :key="index" @click="SelectSkin(index,0)">
        </SkinSelector> 
      </div>
    </div>
    <div class="colorP2 skinSelect">
      <p class='marginPlayer'>Player 2</p>
      <div class='flex wrap'>
        <SkinSelector :name="skin" v-bind:id='"selectSkinP2" + index' v-for="(skin, index) of skins" :key="index" @click="SelectSkin(index,1)">
        </SkinSelector>
      </div>
    </div>
    <input type='button' class='startButton' value='START' @click="StartGame()"/>
  </div>
  <div id='gameScreen' class='hide'>
    <Grid v-for="">
    </Grid>
  </div>
</template>

<script>
import SkinSelector from './SkinSelector.vue'
import Grid from './Grid.vue'
export default {
  name: 'TicTacToe',
  components: {
    SkinSelector
    Grid
  },
 data() {
  return {
    skins: ['\u2717','\u2B58','\u2605', "\u269C", "\u2660", "\u2665", "\u2663", "\u2666"],
    playerSkins: ['',''],
    col: 3,
    row: 3,
  }
 },
 methods: {
    SelectSkin (index,playerNumber){
      let opponentPlayer = 0;
      let opponent;
      let player;
      let i = 0;
      let color = 'blue';
      if (playerNumber == 0){
            opponentPlayer = 1;
            color = 'red';
          }
      if(this.isTheSame(this.skins[index]))
      {
        this.playerSkins[playerNumber] = this.skins[index];
        this.skins.forEach(skin => {
          player = document.getElementById('selectSkinP' + (playerNumber + 1) + i);
          opponent = document.getElementById('selectSkinP' + (opponentPlayer + 1) + i);
          if(this.playerSkins[playerNumber] != skin && this.playerSkins[opponentPlayer] != skin){
            player.style.backgroundColor = 'white';
            opponent.style.backgroundColor = 'white';
          }else if(this.playerSkins[playerNumber] == skin){
            player.style.backgroundColor = 'grey';
            opponent.style.backgroundColor = color;
          }
          i++;
        });

      }

    },
    isTheSame(skin){
      let notEqual = true;
      if(skin == this.playerSkins[0] || skin == this.playerSkins[1])
      {
        notEqual = false;
      }
      return(notEqual)
    },
    StartGame (){
      if(this.playerSkins[0] && this.playerSkins[1]){
        document.getElementById('titleScreen').classList.add('hide');
        document.getElementById('gameScreen').classList.remove('hide');
      }
    },
  },
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

.flex{
  display:flex;
}
.wrap {
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

.hide{
  display:none;
}

</style>
