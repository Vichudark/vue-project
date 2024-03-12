<template>
  <div>
    <h1>login page</h1>
    <!-- {{ Anime}} -->
    <!-- <p v-for="f in Anime" :Key="f" > {{f.mc}} {{ f.anime }}</p> -->
    <!-- <helloworld  v-for="f in Anime" :Key="f" :main-char="f.mc" :anime-name="f.anime" /> -->
    <button @click="count++">Click me</button>
    {{ count }}
  </div>

</template>

<script>
import helloworld from '../components/HelloWorld.vue'
export default {
components:{
    helloworld 
},
data(){
  return{
    Anime:[
      {
        mc:'eren yeager',
        anime:'attack on titan'
      },
      {
        mc:'itadori',
        anime:'jjk'
      },
      {
        mc:'luffy',
        anime:'onepiece'
      }
    ],
    count:0
  }
},
beforeCreate(){
  alert("Before Create");
},
created(){
  alert("Created")
},
beforeMount(){
  console.log("Before mount");
},
mounted(){
  console.log("Mounted");
},
beforeUpdate(){
  console.log("Before Update",this.count);
},
updated(){
  console.log("Updated",this.count);
  console.log("updated");
}
}

</script>

<style>

</style>