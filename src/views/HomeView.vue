<template>
  <div class="home">
    <h1>Payment</h1>
    <stripe-checkout
    ref="checkoutRef"
    mode="payment"
    :pk="publishableKey"
    :line-items="lineItems"
    :success-url="successURL"
    :cancel-url="cancelURL"
    @loading="v =>loading =v"
    
    
    />
    <button class="button" @click="submit">Pay</button>
  </div>
</template>

<script>
  import {StripeCheckout} from '@vue-stripe/vue-stripe'
  export default{
    components:{
      StripeCheckout
    },
    data(){
      this.publishableKey="pk_test_51LiBCPG2ELY3qzVU2NP1ZcO1C4bellgeDyRYxxWoTk7JuIyne1ybCSN2p5MoYYx0O421knk0efCPd0yygX2S3PpS00VFbGfcO5"
      return{
        loading:false,
        lineItems:[
          {
            price:'price_1LiCZ6G2ELY3qzVUYXgdn2Fj',
            quantity:1
          }
        ],
        successURL:'http://localhost8081/success',
        cancelURL:'http://localhost8081/error'
      }
    },
    methods:{
      submit(){
        console.log(this.$refs.checkoutRef);

          // this.$refs.checkoutRef.redirectToCheckout()
          window.location.href = 'https://buy.stripe.com/test_28oeYRaGYeFq2ek6oo'
      }
    }
  }
</script>
<style>

.button{
  align-items: center;
  background-color: #fff;
  border-radius: 12px;
  box-shadow: transparent 0 0 0 3px,rgba(18, 18, 18, .1) 0 6px 20px;
  box-sizing: border-box;
  color: #121212;
  cursor: pointer;
  display: inline-flex;
  flex: 1 1 auto;
  font-family: Inter,sans-serif;
  font-size: 1.2rem;
  font-weight: 700;
  justify-content: center;
  line-height: 1;
  margin: 0;
  outline: none;
  padding: 1rem 1.2rem;
  text-align: center;
  text-decoration: none;
  transition: box-shadow .2s,-webkit-box-shadow .2s;
  white-space: nowrap;
  border: 0;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  width:50%

}

.button:hover {
  box-shadow: #121212 0 0 0 3px, transparent 0 0 0 0;
}
.home{
  display: flex;
  flex-direction: column;
  text-align: center;
  justify-content: center;
  align-items: center;
}
</style>
