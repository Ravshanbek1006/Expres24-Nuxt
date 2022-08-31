<template>
  <div>
    <div class="card-box flex flex-row flex-wrap justify-center items-center">
      <exp-card v-for="(item, index) in express" :key="index" :item="item">
      </exp-card>
    </div>
  </div>
</template>

<script>
import ExpCard from "../components/ExpCard.vue";
export default {
  components: { ExpCard },
  name: "Expres24NuxtIndex",

  data() {
    return {
      express: [],
      massage: "salom",
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

  },

  methods: {},
};
</script>

<style scoped>
</style>
