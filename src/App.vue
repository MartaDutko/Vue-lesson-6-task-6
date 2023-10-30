<template>
<credit-form v-model:cardNumber="cardNumberVal"
v-model:expiryNumber="expiryNumberVal"
v-model:secureCode="secureCodeVal"/>

</template>

<script>
import CreditForm from './components/CreditForm.vue'

export default {
  name: 'App',
  components: {
    CreditForm

  },
  data() {
    return {
      cardNumberVal: null,
      expiryNumberVal:null,
      secureCodeVal:null
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  display: flex;
  justify-content: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
