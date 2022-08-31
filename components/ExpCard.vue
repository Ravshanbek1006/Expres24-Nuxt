<template>
  <div class="card">
    <div class="img-card">
      <img class="w-full full-img" :src="item.detail_picture.src" alt="" />
      <img class="b-img" :src="item.picture.src" alt="" />
    </div>
    <h3 class="text-3xl">
      {{ item.name }}
    </h3>
    <p>sa</p>
    <span class="flex flex-row item-center">
        <svg
        class="w-4"
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        strokeWidth="{1.5}"
        stroke="currentColor"
        className="w-6 h-6"
      >
        <path
          strokeLinecap="round"
          strokeLinejoin="round"
          d="M11.48 3.499a.562.562 0 011.04 0l2.125 5.111a.563.563 0 00.475.345l5.518.442c.499.04.701.663.321.988l-4.204 3.602a.563.563 0 00-.182.557l1.285 5.385a.562.562 0 01-.84.61l-4.725-2.885a.563.563 0 00-.586 0L6.982 20.54a.562.562 0 01-.84-.61l1.285-5.386a.562.562 0 00-.182-.557l-4.204-3.602a.563.563 0 01.321-.988l5.518-.442a.563.563 0 00.475-.345L11.48 3.5z"
        />
      </svg>
       {{ item.reviews.average}} (500+)
    </span>
  </div>
</template>

<script>
export default {
  props: ["item",],
  name: "Expres24NuxtExpCard",
  data() {
    return {
        tip : [],
    };
  },

  mounted() {
    
    this.$axios.get(
      `https://express24.uz/rest/v3/catalog/places-detail/?width=180&height=180&stores_ids[]=5626&stores_ids[]=6377&stores_ids[]=5149&stores_ids[]=4796&stores_ids[]=4869&stores_ids[]=6693&stores_ids[]=6303&stores_ids[]=6935&stores_ids[]=3902&stores_ids[]=6549&stores_ids[]=3524&stores_ids[]=3768&stores_ids[]=5941&stores_ids[]=3425&stores_ids[]=4052&stores_ids[]=4902&stores_ids[]=7179&stores_ids[]=3466&stores_ids[]=4568&stores_ids[]=4848&stores_ids[]=5679&d_width=720&d_height=330&merchantId=1`
    ).then((res)=>{ this.tip = res.data;
    });
    
  },

  methods: {},
};
</script>

<style scoped>
.card {
  width: 440px;
  height: auto;
  margin: 40px 15px;
  padding: 20px;
  transition: all 0.5s ease;
  border-radius: 8px;
}
.card:hover {
  box-shadow: 0 0 30px #888;
  transform: translateY(-20px);
}
h3 {
  margin: 10px 0;
}
.img-card {
  width: 400px;
  height: 200px;
  position: relative;
  top: 0;
  left: 0;
  font-size: 30px;
}
.img-card .full-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.b-img {
  width: 80px;
  height: 80px;
  object-fit: cover;
  border-radius: 16px;
  position: absolute;
  right: 30px;
  bottom: -40px;
  box-shadow: 0 0 10px #555;
}
</style>