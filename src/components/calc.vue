<template>
  <div class="calc">
    
    <div class="main-parent mt-5">
      
      <!-- name -->
      <div class="row mb-3">
        <div class="col-md-12 name">
          {{ name }}
        </div>
      </div>

      <!-- screen  -->
      <div class="row">
        <div class="col-md-12">
          <div class="row">
            
            <div class="col-md-10 screen-cont">
              <input class="screen mb-2" type="text" v-model="screen" @keyup="checkDats()"> 
            </div>

            <div class="col-md-2 action">
              {{ actionScreen }} 
            </div> 
          
          </div>
        </div>
      </div>

      <!-- answer -->
      <div class="row mb-3">
        <div class="col-md-9">
          <p class="answer"> 
            {{ answer }} 
          </p>
        </div>

        <div class="col-md-3 a">
          <input class="btn btn-info dot" type="button" value="." @click="writedot" v-model="dot">
        </div>
      </div>

      <!-- buttons -->
      <div class="row">
        <div class="col-md-12 parents">
          <input class="btn btn-primary nums mb-3" type="button" value=7 @click="writeOnScreen7" v-model="num7">
          <input class="btn btn-primary nums mb-3 ml-3" type="button" value=8 @click="writeOnScreen8" v-model="num8">
          <input class="btn btn-primary nums mb-3 ml-3" type="button" value=9 @click="writeOnScreen9" v-model="num9">
          <input class="btn btn-info mul mb-3 ml-3" type="button" value="*" @click="multiply()"> 
        </div>
      </div>
  
      <div class="row">
        <div class="col-md-12 parents"> 
          <input class="btn btn-primary nums mb-3" type="button" value=4 @click="writeOnScreen4" v-model="num4"> 
          <input class="btn btn-primary nums mb-3 ml-3" type="button" value=5 @click="writeOnScreen5" v-model="num5">
          <input class="btn btn-primary nums mb-3 ml-3" type="button" value=6 @click="writeOnScreen6" v-model="num6">
          <input class="btn btn-info dev mb-3 ml-3" type="button" value="/" @click="division()">
        </div>
      </div>

      <div class="row">
        <div class="col-md-12 parents"> 
          <input class="btn btn-primary nums mb-3" type="button" value=1 @click="writeOnScreen1" v-model="num1"> 
          <input class="btn btn-primary nums mb-3 ml-3" type="button" value=2 @click="writeOnScreen2" v-model="num2">
          <input class="btn btn-primary nums mb-3 ml-3" type="button" value=3 @click="writeOnScreen3" v-model="num3"> 
          <input class="btn btn-info sub mb-3 ml-3" type="button" value="-" @click="substruction()">
        </div>
      </div>

      <div class="row">
        <div class="col-md-12 parents"> 
          <input class="btn btn-primary nums" type="button" value=0 @click="writeOnScreen0" v-model="num0">
          <input class="btn btn-info eq ml-3" type="button" value="C" @click="clear()">
          <input class="btn btn-info add ml-3" type="button" value="+" @click="addition()">
          <input class="btn btn-info eq ml-3" type="button" value="=" @click="equal()">
        </div>
      </div>

    </div>

  </div>
</template>

<script>
export default {
  name: 'Calc',
  data () {
    return {
    // answer
      answer: 'result',
    // name
      name: 'VueJs-calculator',
    // numbers
      num0: '0',
      num1: '1',
      num2: '2',
      num3: '3',
      num4: '4',
      num5: '5',
      num6: '6',
      num7: '7',
      num8: '8',
      num9: '9',
    // action
       screen: '0',
       subScreen: '0',
       actionScreen: '',
       mul: '*',
       div: '+',
       sub: '-',
       add: '+',
       eq: '=',
       c: 'C',
       dot: '.',
       numLength: '0'
    }
  },  

  methods: {
// check if numbers on screen longer then 12 symbhols white error
  checkDats() {
    if (this.screen.length > 12) {
      this.screen = "too long number"
    }
  },
  // numbers
    writeOnScreen0() {
      this.screen = (this.screen + this.num0)
    },
    writeOnScreen1() {
      this.screen = (this.screen + this.num1)
    },
    writeOnScreen2() {
      this.screen = (this.screen + this.num2)
    },
    writeOnScreen3() {
      this.screen = (this.screen + this.num3)
    },
    writeOnScreen4() {
      this.screen = (this.screen + this.num4)
    },
    writeOnScreen5() {
      this.screen = (this.screen + this.num5)
    },
    writeOnScreen6() {
      this.screen = (this.screen + this.num6)
    },
    writeOnScreen7() {
      this.screen = (this.screen + this.num7)
    },
    writeOnScreen8() {
      this.screen = (this.screen + this.num8)
    },
    writeOnScreen9() {
      this.screen = (this.screen + this.num9)
    },
    writedot() {
      this.screen = this.screen + this.dot
    },
    // actions
    multiply () {
      this.actionScreen = this.mul
      if (this.subScreen == "" || this.subScreen == 0){
        this.subScreen = this.screen
        this.screen = ''
      }
      else {
        this.subScreen = (this.subScreen * parseInt(this.screen))
        this.answer = (this.subScreen)
        this.screen = ''
      }
    },
    division () {
      this.actionScreen = this.div
      if (this.subScreen == "" || this.subScreen == 0){
        this.subScreen = this.screen
        this.screen = ''
      }
      else {
        this.subScreen = (this.subScreen / parseInt(this.screen))
        this.answer = (this.subScreen)
        this.screen = ''
      }
    },
    substruction () {
      this.actionScreen = this.sub
      if (this.subScreen == "" || this.subScreen == 0){
        this.subScreen = parseInt(this.screen)
        this.screen = ''
      }
      else {
        this.subScreen = (this.subScreen - parseInt(this.screen))
        this.answer = (this.subScreen)
        this.screen = ''
      }
    },
    addition () {
      this.actionScreen = this.add
      if (this.subScreen == "" || this.subScreen == 0){
        this.subScreen = parseInt(this.screen)
        this.screen = ''
      }
      else {
        this.subScreen = (this.subScreen + parseInt(this.screen))
        this.answer = (this.subScreen)
        this.screen = ''
      }
    },
    equal () {
      this.actionScreen = this.eq
      this.answer = (this.subScreen)
    },
    clear () {
      this.actionScreen = this.c
      this.screen = 0
      this.subScreen = this.screen
      this.answer = 'result'
    },
  }
}
</script>

<style scoped>
 .name{
   font-size: 24px;
 }
 .calc{
   display: flex;
   justify-content: center;
   align-items: center;
 }
 .main-parent{
   background-color: rgb(230, 230, 230);
   box-shadow: 8px 16px #888888;
   width: 350px;
   padding: 20px 20px 20px 20px;
   border-radius: 5px;
   border: 2px black solid;
 }
 .screen-cont{
   margin: 0;
   padding: 0;
 }
 .screen{
   background-color: white;
   padding: 5px;
   color: #000;
   font-size: 28px;
   margin-left: 20px;
   text-align: left;
   width: 80%;
   height: 50px;
   border-radius: 5px;
   border: 2px black solid;
 }
 .action{
   background-color: white;
   display: flex;
   justify-content: center;
   align-items: center;
   font-size: 24px;
   margin-left: -22px;
   width: 20%;
   height: 50px;
   border: 2px black solid;
   border-radius: 5px;
 }
 .answer{
   background-color: white;
   margin: 5px;
   border: 2px black solid;
   border-radius: 5px;
 }
 .a{
   display: flex;
   align-self: flex-end;
 }
 .parents{
   display: flex;
   flex-wrap: nowrap;
 }
 .nums{
   border-radius: 10px;
   box-shadow: 4px 5px 10px blue;
   margin: 5px;
   padding: 5px;
   width: 25%;
   height: 60px;
 }
 .eq, .sub, .dev, .add, .mul{
   border-radius: 10px;
   box-shadow: 4px 5px 10px cyan;
   margin: 5px;
   padding: 5px;
   width: 25%;
 }
 .dot{   
   border-radius: 10px; 
   display: flex;
   justify-content: center;
   align-items: center;
   box-shadow: 4px 5px 10px cyan;
   padding: 5px;
   width: 30px;
   height: 30px;
 }
</style>
