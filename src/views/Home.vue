<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">

    <input class="input" v-model="letters" maxlength="10">
    <HelloWorld :letters="letters"/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import HelloWorld from '@/components/HelloWorld.vue' // @ is an alias to /src

@Component({
  components: {
    HelloWorld
  }
})
export default class Home extends Vue {
  public letters: string = '';


}
</script>


<style> 

body {
  background: #42b983;
}
input { 
  display: flex;
  flex: 1;
  width: 300px;
  height: 50px;
  margin: auto;
  font-size: 30px;
}

</style>
