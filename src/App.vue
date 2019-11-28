    <div id="app">
      <products-list :products="products"></products-list>
      <products-list :products="products" :product-renderer="imageRenderer"></products-list>
    </div>
    <script src="vue.js"></script>
    <script>
      Vue.component('products-list', {
        props: {
          products: {
            type: Array,
            required: true
          },
          productRenderer: {  // <-- Here's our new prop
            type: Function,
            default (h, product) { // <-- By default just print the name
              return product.name
            }
          }
        },
        render(h) {
          return h('ul', [
            this.products.map(product =>
              h('li', [this.productRenderer(h, product)]) // use our new prop
            )
          ])
        }
      })
      new Vue({
        el: '#app',
        data: {
          products: [{
            name: 'Magnifying Glass',
            image: 'magnify.png'
          }, {
            name: 'Light Bulb',
            image: 'bulb.png'
          }],
          imageRenderer(h, product) { // <-- The imageRenderer I'm passing in
            return [
              h('img', {
                attrs: {
                  src: product.image
                }
              }),
              ' ',
              product.name.toUpperCase()
            ]
          }
        }
      })
    </script>