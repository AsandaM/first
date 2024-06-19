<template lang="">
  <div>
    <h1>Counter -> <span>{{counter}}</span></h1>
    <button @click="increment()">Increment</button>
    <button @click="decrement()">Decrement</button>

    <!-- Attach javascriot value to an attribute tag -->
    <img :src="imgURL"> 
  </div>

  <div>
    <!-- Class styling binding -->
     <h4 :class="{hello:check}">Conditional rendering</h4>
     <!-- Conditional rendering -->
    <h1 v-if="check">The value is true</h1>
    <h1 v-else>The value is false</h1>
    <button @click="change()">Change state</button>

    <!-- conditonal rendering -->
    <h1 v-show="check">This contains the v-shows</h1>
    <ul>
      <!-- <li v-for="sport in sports" :key="sport">{{sport}}</li> -->
      <li v-for="({message},index) in objects" :key="index">{{message}}</li>
    </ul>
    <!-- one way data binding -->
    <h3>{{oneWayText}}</h3>
    <!-- two way data binding -->
    <h3>{{twoWayText}}</h3>
    <input type="text" v-model="twoWayText">

  </div>

  <!-- <info-comp first-name="hehe" last-name="hehehehe"/>
  <info-comp first-name="hehe1"/>
  <info-comp :object-data='singleObject'/> -->
  <info-comp>
    Hehehe I am using slots
  </info-comp>
  <slot-comp>
    <template #slotTitle>
      Card Slot
    </template>
    <template #default>
      <img :src="imgURL">
    </template>
  </slot-comp>
</template>
<script>
import InfoComp from '../components/InfoComp.vue'
import SlotComp from '../components/SlotComp.vue'
export default {
  data(){
    return{
      counter: 0,
      imgURL: 'https://hatrabbits.com/wp-content/uploads/2017/01/random.jpg',
      check:true,
      sports:['soccer','netball','volleyball'],
      objects: [
        {message:'Hello There 1', id:1},
        {message:'Hello There 2', id:2},
        {message:'Hello There 3', id:3}
      ],
      singleObject:{
        name: 'Asanda',
        surname:'Mehlo'
      },
      oneWayText: 'hehe',
      twoWayText: 'hehe2.0'
    }
  },
  components:{
    InfoComp,
    SlotComp
  },
  methods:{
    increment(){
      this.counter++
    },
    decrement(){
      this.counter--
    },

    change(){
      this.check = !this.check
    }
  }
}
</script>
<style scoped>
  h1{
    color:blue
  }

.hello{
  color:orange
}
img{
  width: 300px;
}
</style>