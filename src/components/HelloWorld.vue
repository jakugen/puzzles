<template>


  <div class="container">
    
    <div class="mt-2">
      <b-form>
        <b-form-group
          description="">

          <b-form-input
            type="text"
            placeholder="FEN"
            v-model="fen"
            required ></b-form-input>
          </b-form-group>

          <b-form-group>
            
          </b-form-group>
      </b-form>
    </div>
    
    <label class="small muted">yay</label>
    <b-button variant="success" class="button" style="margin-top:10px;margin-bottom:40px" @click="next">NEXT</b-button>

    <Board :fen="fen"/>

  </div>
  
</template>

<script>
import Board from '@/components/Board.vue'
import { getFens } from '../fens'


export default {
  name: 'HelloWorld',
  components: {
    Board
  },
  props: {
    msg: String,
  },
  mounted() {
    this.fens = getFens()
  },
  data() {
    return {
      fen: null,
      fens: null
    }
  },
  methods: {
    next(){
      var rndFen = this.getRandomInt(this.fens["iva_b1"].length);
      this.fen = this.fens["iva_b1"][rndFen]
    },
    getRandomInt(max) {
      return Math.floor(Math.random() * max);
    },

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

.button {
    width:100%;
    display:block;
    margin-left: auto;
}
</style>
