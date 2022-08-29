<template>
  <div id='titleScreen' class='titleScreen court'>
    <div class='flex'>
      <div class="skinSelect colorP1 flex justifySelect">
          <SpriteSelector :name='playerSkins[0]' class='idle'>
          </SpriteSelector>
        <div class='flex wrap'>
          <SkinSelector :name="skin" v-bind:id='"selectSkinP1" + skin' v-for="(skin, index) of defenceSkins" :key="index" @click="SelectSkin(index,0)">
          </SkinSelector> 
        </div>
      </div>
      <div class="skinSelect colorP2 flex justifySelect">
        <div class='flex wrap'>
          <SkinSelector :name="skin" v-bind:id='"selectSkinP2" + skin' v-for="(skin, index) of prosecutorSkins" :key="index" @click="SelectSkin(index,1)">
          </SkinSelector>
        </div>
        <SpriteSelector :name='playerSkins[1]' class='idle'>
        </SpriteSelector>
      </div>
    </div>
    <input type='button' class='startButton' value='START' @click="StartGame()"/>
  </div>
  <div id='gameScreen' class='hide flex justifySelect court'>
    <SpriteSelector :name='playerSkins[0] + this.state[0]' class='animation left'>
    </SpriteSelector>
    <div class='grid'>
      <GridGame :row="this.row" v-bind:id='"Box" + n'  v-for="n in (col*row)" :key="n" @click="PlaceSymbol(n)">
      </GridGame>
    </div>
    <SpriteSelector :name='playerSkins[1] + this.state[1]' class='animation'>
    </SpriteSelector>
    <div id='EndGame' class='absolute hide'><input type='button' value='Rejouer' class='gameButton' @click="RestartGame()"/><input type='button' value='Ecran titre' class='gameButton' @click="ReturnTitle()"/></div>
  </div>
</template>

<script>
import SpriteSelector from './SpriteSelector.vue'
import SkinSelector from './SkinSelector.vue'
import GridGame from './GridGame.vue'
export default {
  name: 'TicTacToe',
  components: {
    SpriteSelector,
    SkinSelector,
    GridGame
  },
 data() {
  return {
    defenceSkins: ['phoenix','mia','gregory','apollo'],
    prosecutorSkins: ['hunter','franziska','manfred','godot','payne','klavier'],
    playerSkins: ['',''],
    token: ['GotIt','HoldIt','Objection','TakeThat'],
    state: ['0','0'],
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
      if (playerNumber == 0){
        this.playerSkins[playerNumber] = this.defenceSkins[index];
        this.defenceSkins.forEach(element => {
          if(element != this.defenceSkins[index]){
            document.getElementById('selectSkinP1' + element).style.backgroundColor = "white";
          }else{
            document.getElementById('selectSkinP1' + this.defenceSkins[index]).style.backgroundColor = "grey";
          }
        });
      }else{
        this.playerSkins[playerNumber] = this.prosecutorSkins[index];
        this.prosecutorSkins.forEach(element => {
          if(element != this.prosecutorSkins[index]){
            document.getElementById('selectSkinP2' + element).style.backgroundColor = "white";
          }else{
            document.getElementById('selectSkinP2' + this.prosecutorSkins[index]).style.backgroundColor = "grey";
          }
        });
      }
    },
    StartGame (){
      if(this.playerSkins[0] && this.playerSkins[1]){
        document.querySelector('.grid').style.setProperty('--col', this.col);
        document.querySelector('.grid').style.setProperty('--row', this.row);
        document.getElementById('titleScreen').classList.add('hide');
        document.getElementById('gameScreen').classList.remove('hide');
        this.state[0] = Math.floor(Math.random() * 3);
      }
    },
    PlaceSymbol(index){
      let box = document.getElementById('Box' + index);
      let randomNumber = Math.floor(Math.random() * 4);
      if(!box.title && this.turnPlayer < 9){
        if(this.turnPlayer % 2 == 0){
          this.state[0] = 0;
          this.state[1] = Math.floor(Math.random() * 3);
          box.classList.add('blue'+ this.token[randomNumber]);
          box.title = 'done';
          this.player1Check += index;
        }else{
          this.state[0] = Math.floor(Math.random() * 3);
          this.state[1] = 0;
          box.classList.add('red' + this.token[randomNumber]);
          box.title = 'done';
          this.player2Check += index;
        }
        if(this.turnPlayer >= 4){
            for(let element in this.winCombinations){
              let Win = this.winCombinations[element].every(this.checkIfWin);
              if(Win == true){
                if(Win == true){
                  if(this.turnPlayer % 2 == 0){
                      this.state[0] = 4;
                      this.state[1] = 3;

                  }else{
                      this.state[0] = 3;
                      this.state[1] = 4;
                  }
                }
                this.turnPlayer = 9;
                document.getElementById('EndGame').classList.remove('hide');
              }
            }
            if(this.turnPlayer == 8){
                this.state[0] = 3;
                this.state[1] = 3;
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
    RestartGame(){
      let box;
      this.state[0] = 0;
      this.state[1] = 0;
      let n=0;
      for(let i=0; i<this.col*this.row; i++){
        n++;
        box = document.getElementById('Box' + n);
        box.setAttribute('class', 'tokenSize');
        box.removeAttribute('title');
        document.getElementById('EndGame').classList.add('hide');
        this.turnPlayer = 0;
        this.player1Check = [];
        this.player2Check = [];
      }
    },
    ReturnTitle(){
      this.RestartGame();
      document.getElementById('titleScreen').classList.remove('hide');
      document.getElementById('gameScreen').classList.add('hide');
    }
  },
}
</script>
<style scoped>

.skinSelect{
  width:50%;
  height:90vh;
}

.flex{
  display:flex;
}

.justifySelect{
  justify-content: space-between;
}
.wrap {
  flex-wrap:wrap;
  width:50vh;
  justify-content:center;
  align-content:start;
}

.marginPlayer {
  margin-top:0;
}

.startButton{
  font-size:8vh;
  height:10vh;
}

.gameButton{
  font-size:5vh;
  height:7vh;
}

.colorP1{
  background:  rgba(0, 0, 255, .3);
}

.colorP2{
  background:  rgba(255, 0, 0, .3);
}

.left{
  align-items:left;
}

.hide{
  display:none;
}

.absolute{
  position:absolute;
  margin-left: auto;
  margin-right: auto;
  bottom:0;
  width:100%
}

.grid{
  --col: 3;
  --row: 3;
  display: grid;
  grid-template-columns: repeat(var(--col) , 1fr);
  height: 50vh;
   margin: auto;
}

.titleScreen {
  width:auto;
  align:center;
}

.court{
  background-image:url(../assets/EcranTitre.webp);
  background-size:100% 100%;
  height:100vh;
}


</style>
