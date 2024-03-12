<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" /> 
    <p v-if=" Ifpurchased > 5 ">Purchased</p>
    <p v-else-if=" Ifpurchased > 0 ">Few stocks</p>
    <p v-else>Out of stock</p>
    <ol>
      <li v-for="(f,index) in fruits" :key="index">{{index}} {{ f }}</li>
      <input type="button" value="clickme" v-on:click="count++">
      {{ count }}

      <input type="button" value="funcall" @click="myfunc()">
    </ol>
    <!-- <textarea @input="enterText($event)"  placeholder="enter text" id="" cols="30" rows="10"></textarea> -->
    <br>
    {{ text }}
    <form>
  <div class="mb-3">
    <label for="exampleInputEmail1" class="form-label">Email address</label>
    <input type="email" v-model="EmailId" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
    <div id="emailHelp" class="form-text">We'll never share your email with anyone else.</div>
  </div>
  <div class="mb-3">
    <label for="exampleInputPassword1" class="form-label">Password</label>
    <input type="password" v-model="Password" class="form-control" id="exampleInputPassword1">
  </div>
  <div class="mb-3 form-check">
    <input type="checkbox" v-model="CheckBox" class="form-check-input" id="exampleCheck1">
    <label class="form-check-label" for="exampleCheck1">Check me out</label>
  </div>
  <!-- <button type="submit" class="btn btn-primary">Submit</button> -->
  
</form>
<label for="products">select product  </label>
<input type="text" v-model="productname" placeholder="enter product">
<br><br>
<label for="quantity" >select quantity  </label>
<input type="number" v-model="productquantity" placeholder="quantity">
<ol>
    <li v-for="item in Cart" :key="item">
    
    </li>
  </ol>
  <input type="button" value="submit" @click="enter()">
  {{this.Cart}}
  <br><br>
  <label for="check">agree</label>
  <input type="checkbox" v-model="chckvalue"> {{accepted }}
  <input type="range" min="0" max="100" v-model="rangValue"> {{ rangValue }}
  </div>
   
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "HomeView",
  data(){
    return{
     fruits:["orange","apple","pineapple","mango"],   
     count:0,
     Ifpurchased:0,
     name :"",
     text:"",
     Password:"",
     EmailId:"",
     CheckBox:true,
     user:{
      emailid:"",
      password:"",
      checkbox:false,
      
     },
     Cart:[
        {
          name:"nivia",
          quantity:5
        }
     ],
     productname:null,
     productquantity:null,
     chckvalue:false,
     rangValue:60
    }
  },
  computed:{
    accepted(){
    if(this.chckvalue){
       return 'yes'
    }else{
      return 'no'
    }
  },  
 
  },
   watch:{
    rangValue(vaLue){
      console.log(vaLue);
      if(vaLue >0 && vaLue<40){
       this.rangValue =40
      }
    }
   },
  mounted(){
    console.log(this.chckvalue,'checkvalue');
    if(this.chckvalue){
      console.log('yes');
    }else{
     console.log('no');
    }
  },
  methods:{
    myfunc(){
      console.log("hello");
      this.name="vishwa"
      console.log("hello"+" "+this.name);
    },
    enterText(event){
      console.log(event);
      this.text=event.target.value

    },
    // login(){
    //   if((this.EmailId=="") &&(this.Password=="")&&(this.CheckBox==false)){
    //        alert("page cannot be empty")
    //   }else{
    //     console.log(this.EmailId);
    //   console.log(this.Password);
    //   console.log(this.CheckBox);
    //   }
    
    // }
    login(){
      console.log(this.EmailId);
      console.log(this.Password);
      console.log(this.CheckBox);
      
      this.user.emailid=this.EmailId,
      this.user.password=this.Password,
      this.user.checkbox=this.CheckBox
      console.log(this.user);
    },
    enter(){
       console.log(this.Cart);
       let cartlist={
        name:this.productname,
        quantity:this.productquantity
      
       }
       console.log(cartlist);
      this.Cart.push(cartlist)
      console.log(this.Cart);
      this.productname=null,
      this.productquantity=null
    }
  }
  
};
</script>
<style>
ol{
  list-style-type: none;
}
</style>
