<template>
  <div class = "counter">
    <div class = "row text-center">
      <h1>{{$store.state.counter.count}}</h1>
      <h3>Counter is <span>{{ IsEvenOrOdd }}</span> <span v-show="IsPrimeCounter"> &amp; prime number</span></h3>
      <h5>Total Clicks: {{$store.state.counter.click}} out of {{ $store.state.counter.maxClick }}</h5>

      <button class = "btn btn-success" @click = "increment" :disabled = IsClickLimitDone>+</button>
      <button class = "btn btn-danger" @click = "decrement" :disabled = IsClickLimitDone>-</button>


      <p class = "text-danger" v-show = "IsClickLimitDone">You clicked 25 times.you have to reset it
          
      </p>
      <h4>check below if you clicked 25 times</h4>
      <button class = "btn btn-warning" v-show="IsClickLimitDone" @click = "enableButtons">Reset</button>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'
export default {
  name: 'Counter',
  computed: {
    ...mapGetters([
      'IsEvenOrOdd',
      'IsClickLimitDone',
      'IsPrimeCounter'
    ]),
    test() {
      return 'This is test data from computed method'
    }
  },
  methods: {
    ...mapActions([
      'increment',
      'decrement',
      
      'enableButtons'
    ])
  }
}
</script>


<style>

button{
    padding: 20px;
    background-color: black;
    color: white;
    margin: 2px;
}
h3{
    background-color: rgb(49, 12, 136);
    color: white;
}
p{
    background-color: rgb(182, 9, 9);
    color:white
}
.counter{
    margin-bottom: 50px;
}
h4{
    padding: 10px;
    margin: 5px;
    border: 2px solid red;
}
</style>