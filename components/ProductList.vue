<template>
  <div>
    <div v-for="(item, index) in productList"
         :key="index">
      <nuxt-link :to="{path: '/pd/ProductDetail', query: {pdNum: item.pdNum}}">
        <Card :product="item"/>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
import Card from "./Card";
export default {
  name: "ProductList",
  components: {Card},
  props: ['selectedCategory'],
  data(){
    return{
      productList: []
    }
  },
  mounted() {
    this.fetchProductList();
  },
  watch:{
    selectedCategory(val){
      console.log('watch', val)
      if(val){
      this.fetchProductList();
      }
    }
  },
  methods:{
    fetchProductList(){
      this.$axios.get(`/api/selectProductList`, {params:{cateNum: this.selectedCategory}})
        .then((res) => {
          this.productList = res.data
          console.log('productList', res)
        })
    }
  }
}
</script>

<style scoped>

</style>
