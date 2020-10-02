<template>
  <div class="kachel-grid" v-if="typeof kacheln[1] != 'undefined'">
    <div class="kachel-wrapper" v-bind:class="{one:kachel.size == 1, two:kachel.size == 2, three:kachel.size == 3, four:kachel.size == 4}" v-for="kachel in kacheln" :key="kachel.id">
            <h3>{{kachel.category}}</h3><br>
            {{kachel.text}}
    </div>
  </div>
</template>

<script>
export default {
  name: 'corona',
  data() {
    return{
      kacheln:[]
    }
  },
  created(){  
    fetch(`http://localhost:3000/kacheln`)
      .then(res => {
        return res.json();
      }).then(this.setResults);
  },
  methods:{
  setResults (results){
    this.kacheln = results;
    console.log(this.kacheln)

  }}
}
</script>

<style scoped>
*{
    box-sizing:border-box
}
    .kachel-grid{
        display: grid;
        flex-wrap: wrap;
        width: 80vw;
        margin: auto;
        background-color:rgb(139, 139, 139);
        grid-template-columns: 16vw 16vw 16vw 16vw 16vw;
        grid-template-rows: 16vw 16vw 16vw 16vw 16vw 16vw 16vw 16vw 16vw 16vw;
        grid-auto-flow: dense;
    }
    .one{
        width: 15vw ;
        height:15vw ;
        background-color: rgb(16, 0, 160);
        margin: 0.5vw;
    }
    .two{
        grid-row: span 2;
        width: 15vw ;
        height:31vw;
        background-color: rgb(255, 0, 0);
        margin: 0.5vw;
    }
    .three{
        grid-column: span 2;
        width: 31vw;
        height:15vw;
        background-color: rgb(2, 97, 18);
        margin: 0.5vw;
    }
    .four{
        grid-column: span 2;
        grid-row: span 2;
        width: 31vw;
        height:31vw;
        background-color: rgb(185, 196, 31);
        margin: 0.5vw;

    }
        @media only screen and (max-width: 1000px) {
    .kachel-grid{
        display: grid;
        flex-wrap: wrap;
        width: 100vw;
        margin: auto;
        background-color:rgb(139, 139, 139);
        grid-template-columns: 32vw 32vw 32vw;
        grid-template-rows: 33.33vw 33.33vw 33.33vw 33.33vw 33.33vw 33.33vw;
        grid-auto-flow: dense
    }
    .one{
        width: 31vw;
        height:31vw;
        background-color: rgb(16, 0, 160);
        margin: 0.5vw;
    }
    .two{
        grid-row: span 2;
        width: 32.33vw;
        height:65.66vw;
        background-color: rgb(255, 0, 0);
        margin: 0.5vw;
    }
    .three{
        grid-column: span 2;
        width: 65.66vw;
        height:32.33vw;
        background-color: rgb(2, 97, 18);
        margin: 0.5vw;
    }
    .four{
        grid-column: span 2;
        grid-row: span 2;
        width: 65.66vw;
        height:65.66vw;
        background-color: rgb(185, 196, 31);
        margin: 0.5vw;

    }
}
    @media only screen and (max-width: 500px) {
    .kachel-grid{
        display: grid;
        flex-wrap: wrap;
        width: 100%;
        margin: auto;
        background-color:rgb(139, 139, 139);
        grid-template-columns: 50vw 50vw;
        grid-template-rows: 50vw 50vw 50vw 50vw  50vw 50vw  50vw 50vw  50vw 50vw ;
        grid-auto-flow: dense
    }
    .one{
        width: 50vw;
        height:50vw;
        background-color: rgb(16, 0, 160);
    }
    .two{
        grid-row: span 2;
        width: 50vw;
        height:100vw;
        background-color: rgb(255, 0, 0);
    }
    .three{
        grid-column: span 2;
        width: 100vw;
        height:50vw;
        background-color: rgb(2, 97, 18);
    }
    .four{
        grid-column: span 2;
        grid-row: span 2;
        width: 100vw;
        height:100vw;
        background-color: rgb(185, 196, 31);

    }
}
</style>