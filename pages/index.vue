<template>
  <div>
    <h1 class="text-center text-5xl mt-20 font-black" >Новости и акции</h1>
    <div class="flex flex-row flex-wrap justify-center items-center">
      <news-sale
        v-for="(sale, index) in product"
        :key="index"
        :sale="sale"
      ></news-sale>
    </div>
    <div>
      <h2 class="text-center text-5xl font-bold mt-20">Все рестораны</h2>
      <div class="card-box flex flex-row flex-wrap justify-center items-center">
        <exp-card v-for="(item, index) in express" :key="index" :item="item">
        </exp-card>
      </div>
    </div>
  </div>
</template>

<script>
import ExpCard from "../components/ExpCard.vue";
import NewsSale from "../components/NewsSale.vue";
export default {
  components: { ExpCard, NewsSale },
  name: "Expres24NuxtIndex",

  data() {
    return {
      express: [],
      product: [],
    };
  },

  mounted() {
    this.$axios
      .get(
        `https://express24.uz/rest/v3/catalog/places-meta?root_category_id=1&d_width=720&d_height=330&limit=21&offset=0&cacheTime=600`
      )
      .then((res) => {
        this.express = res.data.places;
      });
    this.$axios
      .get(
        `https://express24.uz/rest/v2/catalog/promotions?width=480&height=300&rootCategoryId=1`
      )
      .then((res) => {
        this.product = res.data;
        console.log(res.data);
      });
  },

  methods: {},
};
</script>

<style scoped>
</style>
