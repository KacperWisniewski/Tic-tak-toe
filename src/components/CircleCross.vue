<template>
  <div class="game">
    <h1>Tick-Tack-Toe game created with Vue.js</h1>
    <h3>Turn {{ gameTurn}}</h3>
    <h3>Player {{ playerTurn }}</h3>
    <div v-if="gameTurn === 10 && playerWin === 0" class="score">
      draw
    </div>
    <div v-if="playerWin !== 0" class="score">
      Player {{playerWin}} win game!
    </div>
    <div v-if="gameTurn!==10 && playerWin === 0" class="score">
      the match is underway
    </div>
    <div class="holder">
      <div class="place" v-for="box in boxes" @click="changeSign(box)">
        <i v-if="box.sign === 1" class="fas fa-times"></i>
        <i v-else-if="box.sign === 2" class="far fa-circle"></i>
        <i v-else class="far fa-circle" style="color: transparent"></i>
      </div>
    </div>
    <div class="button" v-if="gameTurn === 10 || playerWin !== 0" @click="playAgain()">Play Again</div>
  </div>
</template>

<script>
export default {
    name: 'CircleCross',
    data () {
      return {
          playerWin:0,
          gameTurn:1,
          playerTurn: 1,
          boxes:[
              {
                  id: 1,
                  sign: 0,
              },
              {
                  id: 2,
                  sign: 0,
              },
              {
                  id: 3,
                  sign: 0,
              },
              {
                  id: 4,
                  sign: 0,
              },
              {
                  id: 5,
                  sign: 0,
              },
              {
                  id: 6,
                  sign: 0,
              },
              {
                  id: 7,
                  sign: 0,
              },
              {
                  id: 8,
                  sign: 0,
              },
              {
                  id: 9,
                  sign: 0,
              },
          ]
      }
    },
    methods:{
        playAgain(){
          this.playerTurn = 1
          this.gameTurn = 1
          this.playerWin = 0
          for(let i =0; i < 9; i++){
              this.boxes[i].sign=0
          }
        },
        changeSign(box){
            if(box.sign === 0){
              box.sign = this.playerTurn
              if(this.playerTurn === 1){
                  this.playerTurn = 2
              }
              else if(this.playerTurn === 2){
                  this.playerTurn = 1
              }
              this.gameTurn++
            }
            for(let i=0; i<3; i++) {
                if (this.boxes[(i*3)].sign === this.boxes[((i*3)+1)].sign && this.boxes[(i*3)].sign === this.boxes[((i*3)+2)].sign) {
                    this.playerWin = this.boxes[(i*3)].sign
                    break
                }
                else if (this.boxes[i].sign === this.boxes[(i+3)].sign && this.boxes[i].sign === this.boxes[i+6].sign) {
                    this.playerWin = this.boxes[i].sign
                    break
                }
                else if (this.boxes[0].sign === this.boxes[4].sign && this.boxes[0].sign === this.boxes[8].sign) {
                    this.playerWin = this.boxes[0].sign
                    break
                }
                else if(this.boxes[6].sign === this.boxes[4].sign && this.boxes[6].sign === this.boxes[2].sign){
                    this.playerWin = this.boxes[6].sign
                    break
                }
                else {
                    this.playerWin = 0
                }
            }
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .score{
    text-transform: uppercase;
  }
  .holder{
    margin: 20px auto;
    display: flex;
    max-width: 900px;
    flex-direction: row;
    align-content: space-between;
    flex-wrap: wrap;
    padding: 0;
  }
  .place{
    display: block;
    font-size: 80px;
    flex-grow: 1;
    width: 30%;
    border: 2px solid rgba(0,0,0,0.4);
    padding: 0;
    margin: 0;
  }
  .button{
    margin: 20px auto;
    width: 300px;
    cursor: pointer;
    display: block;
    border: 1px solid #000;
    padding: 5px 0;
    text-transform: uppercase;
  }
</style>
