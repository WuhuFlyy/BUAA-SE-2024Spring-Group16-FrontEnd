<template>
    <el-container>
      <div class="main-content">
        <div class="hot-goods">
          <h3>热门商品</h3>
          <div class="goods-box">
            <GoodsCard
              v-for="(item, i) in hotGoods"
              :key="i"
              :msg="item"
            ></GoodsCard>
          </div>
        </div>
        
        <div class="goods-list">
          <h3>商品列表</h3>
          <div class="goods-box">
            <GoodsCard
              v-for="(item, i) in goods"
              :key="i"
              :msg="item"
            ></GoodsCard>
          </div>
        </div>
        
      </div>
    </el-container>
  </template>
  
  <script>
  import axios from 'axios';
  import Postcard from '../../assets/postcard.jpg';
  import Postcard2 from '../../assets/postcard2.jpg';
  
  export default {
    data() {
      return {
        Postcard,
        Postcard2,
        goods: [],
        hotGoods: [], 
        goodsList: [], 
      };
    },
    methods: {
      getAllGoods() {
        this.goods = [
          {
            productId: 1,
            productName: 'Test Goods',
            productImageBig: this.Postcard,
            salePrice: 114514.19,
            storage: 100,
            sales: 50,
          },
          {
            productId: 2,
            productName: 'Test Goods 2',
            productImageBig: this.Postcard2,
            salePrice: 11.19,
            storage: 200,
            sales: 150,
          },
          {
            productId: 3,
            productName: 'Test Goods 3',
            productImageBig: this.Postcard,
            salePrice: 4514.19,
            storage: 50,
            sales: 30,
          },
          {
            productId: 4,
            productName: 'Test Goods 4',
            productImageBig: this.Postcard,
            salePrice: 810.114,
            storage: 300,
            sales: 280,
          },
        ];
  
        // 这里先假设选取销量大于100的商品作为热门商品，以体现其展示效果，后续可再更改具体逻辑
        this.hotGoods = this.goods.filter((item) => item.sales > 100);
  
        
        this.goodsList = this.goods.map(item => ({
          name: item.productName,
          price: item.salePrice,
          storage: item.storage,
          sales: item.sales,
        }));
      },
      editGoods(row) {
        console.log('编辑商品:', row);
        
      },
      setHotGoods(row) {
        console.log('设为热门商品:', row);
        
      },
    },
    mounted() {
      this.getAllGoods();
    },
  };
  </script>
  
<style scoped>
.el-container {
  display: flex;
}

.main-content {
  flex: 1;
  padding: 20px;
}

.goods-box {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.goods-box > GoodsCard {
  flex: 1 1 calc(25% - 20px); 
  box-sizing: border-box; 
  max-width: calc(25% - 20px); 
}
  
.hot-goods, .goods-list {
  width: 80%; 
  margin: 0 auto; 
  padding: 20px; 
}
  
h3 {
  margin-bottom: 16px;
}
  
.el-table {
  margin-top: 20px;
}
</style>
  