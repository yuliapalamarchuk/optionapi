<template>
  <h1 class="v-catalog_title">Hello I`m catalog</h1>
  <div class="v-catalog">
    <router-link :to="{ name: 'cart', params: { cart_data: CART } }">
      <div class="v-catalog_link_to_cart">
        <i class="medium material-icons">shopping_cart</i>
        {{ CART.length }}
      </div>
    </router-link>
    <div class="v-catalog_list">
      <vCatalogItem
        v-for="product in PRODUCTS"
        :key="product.article"
        :product_data="product"
        @addToCart="addToCart"
      />
    </div>
  </div>
</template>

<script>
import vCatalogItem from "./v-catalog-item.vue";
import { mapActions, mapGetters } from "vuex";
export default {
  name: "v-catalog",
  components: { vCatalogItem },
  props: {},
  data() {
    return {};
  },
  computed: {
    ...mapGetters(["PRODUCTS", "CART"]),
  },
  methods: {
    ...mapActions(["GET_PRODUCTS_FROM_API", "ADD_TO_CART"]),

    addToCart(data) {
      this.ADD_TO_CART(data);
      console.log(data);
    },
  },
  mounted() {
    this.GET_PRODUCTS_FROM_API().then((response) => {
      if (response.data) {
        console.log("Данные пришли");
      }
    });
  },
};
</script>

<style lang="scss">
.v-catalog,
.v-catalog_list {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  align-items: center;
}

.v-catalog_link_to_cart {
  position: absolute;
  top: 10px;
  right: 15px;
  padding: 15px;
}
.v-catalog_title {
  margin: 0;
  padding: 15px 0;
  color: white;
}
</style>