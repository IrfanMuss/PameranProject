<template>
 <div class="piw">
  <selection>
  <div class="container mt-5">
    <div v-if="cartItems.length === 0" class="alert alert-info">
      Your shopping cart is empty!
    </div>
    <div v-else>
      <h2>Shopping cart</h2>
      <table class="table">
        <thead>
          <tr>
            <th>Product</th>
            <th>Price</th>
            <th>amount</th>
            <th>Total</th>
            <th>action</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item, index) in cartItems" :key="index">
            <td>{{ item.name }}</td>
            <td>$ {{ item.price }}</td>
            <td>
              <input type="number" v-model="item.quantity" min="1" @input="updateCart" />
            </td>
            <td>$ {{ item.quantity * item.price }}</td>
            <td>
              <button class="btn btn-danger" @click="removeItem(index)">Delete</button>
            </td>
          </tr>
        </tbody>
      </table>
      <h3>Total: $ {{ total }}</h3>
      <button class="btn btn-primary" @click="checkout">Checkout</button>
    </div>
  </div>
</selection>
</div>
</template>

<script>
export default {
  data() {
    return {
      cartItems: [
        { name: 'Lenovo IdeaPad 3 14ITL6', price: 504, quantity: 1 },
        { name: 'Acer Aspire 5 (Ryzen 5000) A515-45', price: 410, quantity: 1 },
        { name: 'HP Laptop 15s-fq2503TU', price: 454, quantity: 1 },
        { name: 'Oppo Reno8', price: 411, quantity: 1 },
        { name: 'OPPO Reno9', price: 454, quantity: 1 },
        { name: 'OPPO Reno10', price: 630, quantity: 1 },
        { name: 'Galaxy Tab S9 FE', price: 473, quantity: 1 },
        { name: 'Tab S9FE+', price: 536, quantity: 1 },
        { name: 'Wi-Fi Galaxy Tab S9 FE', price: 410, quantity: 1 },
      ],
    };
  },
  computed: {
    total() {
      return this.cartItems.reduce((total, item) => total + item.quantity * item.price, 0);
    },
  },
  methods: {
    updateCart() {
    },
    removeItem(index) {
    },
    checkout() {
      alert('Checkout berhasil!');
    },
  },
};
</script>