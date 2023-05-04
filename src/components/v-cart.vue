<template>
  <div class="v-cart">
    <router-link :to="{ name: 'catalog' }">
      <div class="v-catalog_link_to_cart basket">
        <i class="medium material-icons basket">shopping_cart</i>
        {{ CART.length }}
      </div>
      <button class="btn v-cart_btn">Back to catalog</button>
    </router-link>

    <p v-if="!CART.length">You haven`t any products</p>

    <vCartItem
      v-for="(item, index) in CART"
      :key="item.article"
      :cart_item_data="item"
      @deleteFromCart="deleteFromCart(index)"
    />
  </div>
</template>

<script>
import vCartItem from "./v-cart-item.vue";
import { mapActions, mapGetters } from "vuex";
export default {
  name: "v-cart",
  components: {
    vCartItem,
  },
  props: {
    cart_data: {
      type: Array,
      default() {
        return [];
      },
    },
  },
  data() {
    return;
  },
  computed: {
    ...mapGetters(["CART"]),
  },
  methods: {
    ...mapActions(["DELETE_FROM_CART"]),
    deleteFromCart(index) {
      this.DELETE_FROM_CART(index);
    },
  },
};
</script>

<style lang="scss">
.v-cart {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  color: grey;
  font-size: 20px;
min-height: 100vh;
display: flex;
flex-direction: column;
justify-content: center;
}

p {
  text-align: center;
  font-size: 26px;
}

.v-cart_btn {
  background: #b32ce3;
  border-radius: 9px;
 color: black;
  border: 1px solid #ffffff;
  cursor: pointer;
  font-weight: 700;
  font-size: 12px;
  box-shadow: 0 0 10px 0 #ffffff;
  transition: 0.7s;
  position: absolute ;
  top: 30px;
  left: 30px;
}

.basket{
    color: #b32ce3;

}
</style>

