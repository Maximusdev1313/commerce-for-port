<script setup>
import { useApiStore } from 'src/stores';
import { ref, toRefs } from 'vue';
const store = useApiStore()
const props = defineProps({
  products: Array,
 
});
const { products } = toRefs(props);
// store.getCategory()
let slide = ref(1)
</script>

<template>
  <div class="container">
    <div class="wrapper row justify-around items-left wrap">
      <div class="card shadow-up-5 q-ma-md column justify-center items-center" v-for="card in products" :key="card">
        <div
          class="discount "
          
        >
        <div v-if="card.chegirma_foizi" class="row justify-between items-center q-mt-sm  text-red text-weight-bold">
          <div class="discount__title">Discount</div>
          <div class="discount__percent">{{ card.chegirma_foizi }} %</div>
        </div>
          
        </div>
        <div class="card__img row justify-center">
          
              <img :src="card.rasmlari[0].link " :alt="card.rasmlari[0].title" >            
          <!-- <div class="card__img_have-not"></div> -->
        </div>
        <div class="card__title text-h6 text-weight-bold text-uppercase text-grey">Title</div>
        <div class="card__price row justify-between text-weight-bold">
          <div class="card__price_old text-grey"> <del>{{ card.eski_narx }}</del> </div>
          <div class="card__price_new text-red">{{card.narx}}</div>
        </div>
        <div class="card__button ">
            <q-btn class="full-width q-my-md" icon="shopping_cart" color="accent">
                <q-tooltip class="bg-accent">Buy</q-tooltip>
                Buy now
            </q-btn>
        </div>
      </div>
    </div>
  </div>
</template>
<style scoped>
.container {
  width: 90%;
  margin: 0 auto;
}
.wrapper {
  width: 100%;
}
.card {
  width: 250px;
  border-radius: 10px;
  background-color: #ffff;
}
.discount {
  width: 90%;
  border-radius: 30px;
  height: 25px;
}

img{
  width: 200px;
  height: 200px;
  margin: 20px 0;
}

.card__price{
    width: 90%;
}
.card__button{
    width: 90%;