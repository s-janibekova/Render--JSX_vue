<template>
  <div class="hello">
     <div>Price: ${{ price }}</div>
      <div>Total: ${{ price * quantity }}</div>
      <div>Taxes: ${{ totalPriceWithTax }}</div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
    price: 15.00,
    quantity: 2,  
    }
  },
  computed: {
      totalPriceWithTax() {
        return this.price * this.quantity*1.03
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
</style>
