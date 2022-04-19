<template>
  <div>상품상세 : {{ productDetail }}</div>
</template>

<script>
export default {
  name: "ProductDetail",
  data(){
    return{
      productDetail: {}
    }
  },
  asyncData(context) {
    console.log('context', context)
    return context.$axios.get('/api/getProductDetail', {params: {pdNum: context.query.pdNum}}).then((res) => {
      console.log('productDetail res', res);
      return {productDetail: res.data};
    })
  },
  head() {
    return {
      title: `상품 상세 페이지 - ${this.productDetail.pdName}`
    }
  },
}
</script>

<style scoped>

</style>
