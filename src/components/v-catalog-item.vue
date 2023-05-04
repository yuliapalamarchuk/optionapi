<template>
  <div class="v-catalog-item">
    <img
      class="v-catalog-item_image"
      :src="require('../assets/images/' + product_data.image)"
      alt="picture"
    />
    <p class="v-catalog-item_name">{{ product_data.name }}</p>
    <p class="v-catalog-item_price">{{ product_data.price }}</p>
    <p class="v-catalog-item_about">{{ product_data.about }}</p>
    <button class="v-catalog-item_btn" @click="addToCart">Add to cart</button>
  </div>
</template>

<script>
export default {
  name: "v-catalog-item",
  props: {
    product_data: {
      type: Object,
      default() {
        return {};
      },
    },
  },
  data() {
    return {};
  },
  methods: {
    addToCart() {
      this.$emit("addToCart", this.product_data);
    },
  },
};
</script>

<style lang="scss">
.v-catalog-item {
  box-shadow: 0 0 12px 0 #ffffff;
  padding: 20px;
  margin: 20px;
  width: 300px;
  background: #b32ce3;
  border-radius: 42px;
  border: 0.5px solid #ffffff;
}

.v-catalog-item_btn {
  background: #b32ce3;
  border-radius: 9px;
  width: 122px;
  height: 36px;
  border: 1px solid #ffffff;
  cursor: pointer;
  font-weight: 700;
  font-size: 12px;
  box-shadow: 0 0 10px 0 #ffffff;
  transition: 0.7s;
  &:hover {
    transform: scale(1.2);
  }
}

.v-catalog-item {
  flex-basis: 40%;
  box-shadow: 0 0 8px grey;
  padding: 20px;
  margin: 20px;
}

.v-catalog-item_image {
  width: 160px;
  display: block;
  margin: 0 auto;
}
</style>