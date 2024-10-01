<template>
  <div id="app">
    <game-board></game-board>
  </div>
</template>

<script>
import GameBoard from './components/GameBoard.vue';

export default {
  components: {
    GameBoard
  }
};
</script>
<style>
body,html{
  background: rgb(191,16,137);
  background: linear-gradient(126deg, rgba(191,16,137,1) 21%, rgba(255,14,88,1) 43%, rgba(14,31,255,1) 69%, rgba(118,223,242,1) 87%);
  background-repeat: no-repeat;
  padding: 0;
  margin: 0;
  height: 100%;
  min-height: 100%;
}
.app{
  display: flex;
justify-content: center;
   background-color: transparent;

}
</style>