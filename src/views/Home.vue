<template>
  <div>
    <h1>Rick and Morty</h1>
      <div class="content">     
        <div class="content-characters" v-for="(character, index) in characters" :key="index">
        <div class="character">
          <img :src="character.image" alt="">
        <div class="info-character">
          <h2>{{ character.name }}</h2>
          <h4>{{ character.gender }}</h4>
          <h4>{{ character.species }}</h4>
          <h4>{{ character.status }}</h4>
        </div>
        </div>
    </div>
    </div>      
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'


export default {
  name: 'Home',
  components: {
  },
  data(){
    return{
      characters: null
    }
  },
  mounted(){
    this.getTwenty();
  },
  methods: {
    getTwenty(){
      axios
        .get('https://rickandmortyapi.com/api/character/1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20')
        .then(res => {
          console.log(res.data)
          (this.characters = res.data)
        })
        .catch(e => {
          console.log(e)
        })      
    }
  }

}
</script>

<style>
body{
  background: #0e2f22;
}
.content{
  display: grid;
  grid-template-columns: 1fr 1fr 1fr 1fr;
  grid-template-rows: 1fr;
  gap: 20px 20px;
}

.content-characters{
  background: #021835;
    padding: 1rem;
    border-radius: 1rem;
    
}
.character{
  display: flex;
}
.info-character{
  display: table-column;
  justify-content: center;
  margin: 0 auto;
}
img{
  max-width: 50%;
  border-radius: 10rem;
}
h1 {
  color: #00ff97;
}
h2 {
  color: #1b1b1b;
  font-weight: bold;
  font-size: 1.2rem;
  padding: 1rem;
  background: #00ff97;
  border-radius: 0.8rem;
}
h4{
  margin: 1rem;
  color: white;
  font-weight: 300;
}

</style>
