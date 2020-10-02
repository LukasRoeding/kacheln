<template>
<div>
    <div class="button-wrapper">
        <button v-on:click="change('1')" class="category-button">Kategorie 1</button>

        <button v-on:click="change('2')" class="category-button">Kategorie 2</button>

        <button v-on:click="change('3')" class="category-button">Kategorie 3</button>

        <button v-on:click="changeBack()" class="category-button">Zurück</button>
    </div>
        <div class="kachel-grid" v-if="typeof kacheln[1] != 'undefined'">
            <div class="kachel-wrapper" 

                v-bind:class="{one:kachel.size == 1, two:kachel.size == 2, three:kachel.size == 3, four:kachel.size == 4}"

                v-for="kachel in kacheln" :key="kachel.id">

                <div class="kachel-text">
                    {{kachel.text}}
                </div>
            </div>
        </div>
</div>
</template>

<script>
export default {
  name: 'kachelgrid',
  data() {
    return{
      kacheln:[],
      kachelnSave: [],
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
    this.kachelnSave = this.kacheln;
    console.log(this.kacheln)
  },
  change(name){
      this.kacheln = [];
        for (let index = 0; index < this.kachelnSave.length; index++) {
            if (this.kachelnSave[index].category == name) {
                this.kacheln.push(this.kachelnSave[index]);
            }
            
        }
      },
    changeBack(){
        this.kacheln = this.kachelnSave;
    }
      }
  }
  
</script>

<style scoped>

    .button-wrapper{
        display: grid;
        grid-template-columns: auto auto auto auto;
        margin:auto;
        width:80%;
    }

    .category-button{
        margin:5px;
        height:40px;
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

    .button-wrapper{
        display: grid;
        grid-template-columns: auto auto;
        grid-template-rows: auto auto;
        margin:auto;
        width:80%;
    }

    .kachel-grid{
        display: grid;
        flex-wrap: wrap;
        width: 90vw;
        margin: auto;
        background-color:rgb(139, 139, 139);
        grid-template-columns: 30vw 30vw 30vw;
        grid-template-rows: 30vw 30vw 30vw 30vw 30vw 30vw;
        grid-auto-flow: dense
    }
    .one{
        width: 29vw;
        height:29vw;
        background-color: rgb(16, 0, 160);
        margin: 0.5vw;
    }
    .two{
        grid-row: span 2;
        width: 29vw;
        height:59vw;
        background-color: rgb(255, 0, 0);
        margin: 0.5vw;
    }
    .three{
        grid-column: span 2;
        width: 59vw;
        height:29vw;
        background-color: rgb(2, 97, 18);
        margin: 0.5vw;
    }
    .four{
        grid-column: span 2;
        grid-row: span 2;
        width: 59vw;
        height:59vw;
        background-color: rgb(185, 196, 31);
        margin: 0.5vw;

    }
}
    @media only screen and (max-width: 500px) {
    .kachel-grid{
        display: grid;
        flex-wrap: wrap;
        width: 94vw;
        margin: auto;
        background-color:rgb(139, 139, 139);
        grid-template-columns: 47vw 47vw;
        grid-template-rows: 47vw 47vw 47vw 47vw  47vw 47vw  47vw 47vw  47vw 47vw 47vw 47vw ;
        grid-auto-flow: dense
    }
    .one{
        width: 46vw;
        height:46vw;
        background-color: rgb(16, 0, 160);
        margin: 0.5vw;
    }
    .two{
        grid-row: span 2;
        width: 46vw;
        height:93vw;
        background-color: rgb(255, 0, 0);
        margin: 0.5vw;
    }
    .three{
        grid-column: span 2;
        width: 93vw;
        height:46vw;
        background-color: rgb(2, 97, 18);
        margin: 0.5vw;
    }
    .four{
        grid-column: span 2;
        grid-row: span 2;
        width: 93vw;
        height:93vw;
        background-color: rgb(185, 196, 31);
        margin: 0.5vw;
    }
}
</style>