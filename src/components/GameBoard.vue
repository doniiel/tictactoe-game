<template>
    <div class="game-board">
        <h1>TIC TAC TOE</h1>
        <h3 class="player">Player:{{currentPlayer}}</h3>
      <div v-for="(row, rowIndex) in board" :key="rowIndex" class="row">
        <div v-for="(cell, colIndex) in row" :key="colIndex" class="cell" @click="makeMove(rowIndex, colIndex)">
          {{ cell }}
        </div>
      </div>
      <div v-if="winner" class="winner">Winner:{{ winnerPlayer }}</div>
      <div v-else-if="draw" class="winner">Draw</div>      
      <div class="button">
        <button @click="resertGame">RESERT</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        board: [
          ['', '', ''],
          ['', '', ''],
          ['', '', '']
        ],
        currentPlayer: 'X',
        winner:false,
        winnerPlayer:'',
        count:0,
        draw:false
      };
    },
    methods: {
      makeMove(row, col) {
        if(this.board[row][col]==='' && !this.winner){
            this.count++;
            this.board[row][col]=this.currentPlayer;
            this.win(row,col,this.currentPlayer);
            this.changePlayer();
        }
        if(this.count===9){
           this.draw=true; 
        }
      },
      changePlayer(){
        this.currentPlayer= this.currentPlayer === 'X'?'O':'X';
      },
      resertGame(){
        this.board =[
          ['', '', ''],
          ['', '', ''],
          ['', '', '']
        ],
        this.winner=false;
        this.winnerPlayer='';
        this.count=0;
        this.draw=0;
        this.currentPlayer='X';
      },
      win(row,col,currentPlayer){
        for(let i = 0;i<3;i++){
            if(this.board[row][i]!==currentPlayer){
                break;
            }
            if(i===2){
                this.winner=true;
                this.winnerPlayer=this.currentPlayer
            }
        }

        for(let i = 0;i<3;i++){
          if(this.board[i][col]!==currentPlayer ){
                 break;
          }
          if(i===2){
            this.winner=true;
            this.winnerPlayer=this.currentPlayer
          }
        }
        if(row===col){
        for(let i = 0;i<3;i++){
            if(this.board[i][i]!=currentPlayer){
                break;
            }
            if(i===2){
                this.winner=true;
                this.winnerPlayer=this.currentPlayer
            }
           }
        }
        if(row+col===2){
            for(let i = 0;i<3;i++){
                if(this.board[i][2-i]!=currentPlayer){
                    break;
                }
                if(i===2){
                this.winner=true;
                this.winnerPlayer=this.currentPlayer
            }
            }
        }
      }
    }
  };
  </script>
  
  <style scoped>
  h1{
    font-size: 35px;
    font-weight: lighter;
    color: white;
    text-shadow: 3px 5px 8px gold;

    text-align: center;
  }
   .game-board {
      padding: 80px 100px;
    }
  
  .row {
   display: flex;
   align-items: center;
   justify-content: center;
   font-family: 'Crafty Girls', cursive;
  }
  
  .cell {
   height: 100px;
   width: 100px;
   display: flex;
  align-items: center;
  justify-content: center;
  font-size: 3rem;
  font-weight: 200;
  border: 1px solid white;
  backdrop-filter: blur(10px);
  box-shadow: 5px 2px 8px white;
  color: white;
  }
  .row > div:hover {
  box-shadow: 2px 2px 34px -5px rgba(0, 0, 0, 0.5);
}
.button{
    margin-top: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
}
.button button{
    outline: none;
    border: none;
    padding: 10px 15px;
    background-color: red;
    color: aliceblue;
    border-radius: 3px;
    font-weight: 700;
    animation: bounce 1s ease-in-out infinite;
}
@keyframes bounce{
    0% {top:0px;}
    50%{
        top:-10px;
        -webkit-box-shadow:0px 10px 13px -7px #000000, 5px 5px 15px 5px rgba(0,0,0,0);
        box-shadow: 0px 10px 13px -7px #000000,5px 5px 15px 5px rgba(0,0,0,0);
    }
    100%{top:0px}
}
.button button:hover{
    color: gold;
    box-shadow: 0 0 5px red,0 0 25px red, 0 0 50px red, 0 0 100px red,0 0 200px red;
}
.player{
    text-align: center;
    color: whitesmoke;
}
.winner{
    margin-top: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    color: white;
    font-size: 50px;
}
.X{
    color: blue;
}
.O{
    color: red;
}
  </style>