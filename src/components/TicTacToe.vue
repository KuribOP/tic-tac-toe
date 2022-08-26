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
  <div id='gameScreen' class='hide gameScreen'>
    <div class='grid'>
      <GridGame v-bind:id='"Box" + n'  v-for="n in (col*row)" :key="n" @click="PlaceSymbol(n)">
      </GridGame>
    </div>
  </div>
</template>

<script>
import SkinSelector from './SkinSelector.vue'
import GridGame from './GridGame.vue'
export default {
  name: 'TicTacToe',
  components: {
    SkinSelector,
    GridGame
  },
 data() {
  return {
    skins: ['\u2717','\u2B58','\u2605', "\u269C", "\u2660", "\u2665", "\u2663", "\u2666"],
    playerSkins: ['',''],
    col: 3,
    row: 3,
    turnPlayer: 0,
    winCombinations: {
      1: ['1','2','3'],
      2: ['4','5','6'],
      3: ['7','8','9'],
      4: ['1','5','9'],
      5: ['3','5','7'],
      6: ['1','4','7'],
      7: ['2','5','8'],
      8: ['3','6','9']
    },
    player1Check: [],
    player2Check: []
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
        document.querySelector('.grid').style.setProperty('--col', this.col);
        document.querySelector('.grid').style.setProperty('--row', this.row);
        document.getElementById('titleScreen').classList.add('hide');
        document.getElementById('gameScreen').classList.remove('hide');
        /*let i = 1;
        for(let nRow = 0; nRow < this.row; nRow++){
          this.boxInGrid['row' + nRow] = { };
          for(let nCol = 0; nCol < this.col; nCol++){
            this.boxInGrid['row'+nRow]['col'+nCol] = i; 
            i++; 
          }
        }*/
      }
    },
    PlaceSymbol(index){
      let box = document.getElementById('Box' + index);
      if(!box.innerHTML){
        if(this.turnPlayer % 2 == 0){
          box.innerHTML = this.playerSkins[0];
          this.player1Check += index;
        }else{
          box.innerHTML = this.playerSkins[1];
          this.player2Check += index;
        }
        if(this.turnPlayer >= 4){
            for(let element in this.winCombinations){
              let Win = this.winCombinations[element].every(this.checkIfWin);
              if(Win == true){
                console.log('win');
              }
            }
          }
        this.turnPlayer += 1;
      }
    },
    checkIfWin(winCombination, index, array){
      let playerWon = false;
      let counter = 0;
      let playerCheck;
      if(this.turnPlayer % 2 == 0){
        playerCheck = this.player1Check;
      }else{
        playerCheck = this.player2Check;
      }
      for(let element of playerCheck){
        if(array.includes(element)){
          counter++;
        }
      }
      if(counter >= 3){ 
        playerWon=true;
      }
      return playerWon;
    },
    //calcul gagnant : n*maxRow+1,n*maxRow+2,n*maxRow+3 ... autant que de col 
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

.gameScreen{
  display:flex;
  justify-content:center;
}

.hide{
  display:none;
}

.grid{
  --col: 3;
  --row: 3;
  display: grid;
  grid-template-columns: repeat(var(--col) , 1fr);
}


</style>
