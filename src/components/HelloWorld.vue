<template>
  <div class="hello">
    

    <div class="tiles">
      <div class="tile actual" v-for="(letter, index) in letters" :key="letter+index">
        {{letter}}
      </div>
    </div>


    <div v-for="word in getMatchingWords()" :key="word">

    <div class="tiles">
        <div class="tile" v-for="(letter, index) in word" :key="letter+index">
          {{letter}}
        </div>
      </div>
    </div>

  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

import allWords from '!raw-loader!../assets/words.txt';
@Component
export default class HelloWorld extends Vue {
  @Prop() private letters!: string;

  public words : string[] =[];

  public mounted() {
    this.words = allWords.split("\n");
  }


  public getMatchingWords() {
    let matching = [];
    const sortedLetters = this.letters.split("").sort((a, b) => a.toLowerCase().localeCompare(b.toLowerCase())).join("");
    for (let word of this.words) {
      word = word.toLowerCase().trim();
      if (word.length > this.letters.length) {
        continue;
      }

      let sortedWord = word.split("").sort((a, b) => a.toLowerCase().localeCompare(b.toLowerCase())).join("");

      if (sortedWord == sortedLetters.substring(0, sortedWord.length)) {
        matching.push(word);
      }
    }

    matching = matching.sort((a, b) => b.length - a.length)
    return matching;
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
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


.tiles {
  display: flex;
  box-sizing: border-box;
  align-items: center;
  justify-content: center;
}
.tile {
  display: flex;
  margin: 10px;
  width: 100px;
  height: 100px;
  background:white;
  color: #42b983;
  font-size: 50px;
  align-items: center;
  justify-content: center;

}


</style>
