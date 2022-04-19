<!-- Please remove this file from your project -->
<template>
  <div data-app class="relative flex items-top justify-center min-h-screen bg-gray-100 sm:items-center sm:pt-0">
    <v-menu
      open-on-hover
      top
      offset-y
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="primary"
          dark
          v-bind="attrs"
          v-on="on"
        >
          카테고리
        </v-btn>
      </template>

      <v-list>
        <v-list-item
          v-for="(item, index) in categoryList"
          :key="index"
        >
          <a @click="selectedCategory = item.cateNum">{{ item.cateName }}</a>
        </v-list-item>
      </v-list>
    </v-menu>
    <ProductList
    :selectedCategory="selectedCategory"
    />
  </div>
</template>

<script>
import ProductList from "./ProductList";
export default {
  name: 'NuxtTutorial',
  components: {ProductList},
  data(){
    return {
      categoryList: [],
      selectedCategory: 1
    }
  },
  mounted() {
    this.$axios.get('/api/selectCategoryList').then((res) => {
      console.log('selectCategoryList', res)
      this.categoryList = res.data;
    })
  }
}
</script>
