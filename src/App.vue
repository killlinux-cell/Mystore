<template>

  <NavView />
  
  <hero-view></hero-view>

  <h1 class="special">Nos articles</h1>

  <!-- Ma grid -->

<!--   <div class="parent">
        <div class="div1">

        </div>
  </div>
 -->
  <!-- Ma grid -->

  
<!-- ARTICLES GRID SECTION -->
   <div class="items-container">

    <div  v-for="item in items" v-bind:key="item.id" class="cards-container" >
      <div class="card" @click="items.isActive = true, 
      clickedItem = [],
      clickedItem.push(item.attributes.name, item.attributes.description, item.attributes.price, item.attributes.thumbnail.data[0].attributes.url),
       console.log(clickedItem)">
        <img class="card-img" :src="`${api_url}${item.attributes.thumbnail.data[0].attributes.url}`" />
        <p class="card-name first-line" id="card-on-hover">{{ item.attributes.name }}</p>
        <p class="card-price second-line" id="card-on-hover">{{ item.attributes.price }} CFA</p>
        <p class="card-desc third-line" id="card-on-hover">{{ item.attributes.description }}</p>
        <p id="item-id" style="display: none;">{{ item.id }}</p>
      </div>
    </div>
    
   </div>
   <!-- ARTICLES GRID SECTION -->

<!-- MODAL VIEW -->
   <div v-if="items.isActive" class="modal-wrapper">

    <ModalView>

      <div class="modal-top">

      <button @click="items.isActive = false" class="close-modal">
        <img src="@/assets/close.png" height="30" width="30">
      </button>
      <h2 style="font-size: 36px;">{{ clickedItem[0] }}</h2>

    </div>
    
      <p>{{ clickedItem[1] }}</p>
      <p style="color:#d32d4d; font-weight: 700; font-size: 1.25em;">{{ clickedItem[2] }} CFA</p>
      <img :src="`${api_url}${clickedItem[3]}`" alt="" height="500" width="800" class="modal-img">
      <button class="add-cart">AJOUTER AU PANIER</button>

    </ModalView>

   </div>
   <!-- MODAL VIEW -->
   



   <FooterView />  
</template>

<script>
import NavView from './components/NavView.vue'
import ModalView from './components/ModalView.vue' 
import heroView from './components/heroView.vue'
import FooterView from './components/FooterView.vue'  
import {useItemStore} from "@/stores/store.js"


export default {
  name: 'App',
  components: {
    NavView,
    ModalView,
    heroView,
    FooterView,  
  },

  data() {
    return {
      items: [],
      api_url: "http://localhost:1337",
      clickedItem: []
    }
  },

  
  beforeMount() {
    const items = useItemStore();
    console.log(items.isActive)
    if (items.articles.length == 0) {
      items.getArticles()
    }

    let articles = items.articles;
    this.items.push(articles)
    this.items = this.items[0]
  },

}
</script>

<style>

/* Ma grid */

.parent {
    display: grid;
    grid-template-columns: 2fr repeat(2, 1fr);
    grid-template-rows: 3fr 2fr;
    grid-column-gap: 10px;
    grid-row-gap: 10px;
}

.div1 { grid-area: 1 / 1 / 2 / 2; }
.div2 { grid-area: 1 / 2 / 2 / 3; }
.div3 { grid-area: 1 / 3 / 2 / 4; }
.div4 { grid-area: 2 / 1 / 3 / 2; }
.div5 { grid-area: 2 / 2 / 3 / 3; }
.div6 { grid-area: 2 / 3 / 3 / 4; }

/* Ma grid */

/* special */
.special{
  text-align: center;
  font-size: 40px;
  font-family: Arial, Helvetica, sans-serif;
  margin: 50px 0;
}

/* gufgueg */


.add-cart {
  border: none;
  padding: 2%;
  border-radius: 40px;
  background-color: #2d74ff;
  color: white;
  font-size: 1.25em;
  transition: 0.2s;
  margin-left: 5%;
  margin-top: 1%;
}

.modal-top {
  display: flex;
  flex-direction: row;
}

.modal-img {
  width: 100%;
}

.close-modal {
  height: fit-content;
  position: relative;
  left: 95%;
  border: none;
  transition: 0.2s;
}

.close-modal:hover {
  filter: invert();
}

.modal-wrapper {
  display: flex;
  flex-direction: column;
}

.add-cart:hover {
  transform: scale(1.1);
}

#app {
  margin: 0;
  padding: 0;
}

.items-container {
  margin-left: 5%;
  width: 100%;
  display: grid;
  grid-template-columns: repeat(3,33.33333%);
}

.first-line {
  opacity: 0;
  transition-duration: 0.45s;
  font-size: 1.75em;
  position: absolute;
  top: 0%;
}
.second-line {
  opacity: 0;
  transition-duration: 1s;
  font-size: 1.5em;
  position: absolute;
  top: 65%;
}
.third-line {
  opacity: 0;
  transition: 1.5s;
  position: absolute;
  top: 80%;
}

.card {
  position: relative;
  transition: 0.45s;
  overflow: hidden;
}

.card-img {
  width: 75%;
  transition: 0.45s;
}


#card-on-hover {
  z-index: 5;
  color: black;
  margin-left: 2%;
}

.card:hover .card-img {
  filter: blur(8px);
  transform: scale(1.1);
}

.card:hover .first-line,
  .card:hover .second-line,
    .card:hover .third-line{
  opacity: 1;
}

body {
  font-family: Roboto;
  margin: 0;
  padding: 0;
  top: 0;
  overflow-x: hidden;
  background-color: #f9f9fa;
}

.each-benef {
  position: relative;
  display: flex;
  justify-content: center;
}

#separation {
  position: relative;
  left: 42%; 
  margin-bottom: 5%;
}


#discounted-price {
  padding-left: 2%;
  text-decoration: line-through;
  color: #6f6f73;
}

#benefit-img {
  margin-left: 40%;
}

#discount-text {
  font-size: 2em;
  color: #d32d4d;
}

.hero-container {
  padding: 0;
  margin-top: -27px;
  background-image: url('@/assets/header-bg.jpg');
  width: 100vw;
  height: 900px;
  background-color: black !important;
  color: white;
}

.head-name {
  font-size: 3.5em;
}

#hero-image {
  z-index: 0;
}

.shop-price {
  display: flex;
  flex-direction: row;
  justify-content:flex-start;
  width: 50%;
}

.hero-content {
  position: relative;
  top: 50%;
  margin-left: 5%;
}

.shop-btn {
  border: none;
  background-color: #2d74ff;
  color: white;
  padding-left: 3%;padding-right: 3%;
  margin-right: 5%;
  font-size: 1.25em;
  transition: 0.2s;
}

.shop-btn:hover {
  transform: scale(1.1);
  background-color: #da5050;
}

.benefits-container {
  padding-top: 5%;padding-bottom: 5%;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}


.benefit-card {
  align-items: center;
  padding: 3%;
  background-color: white;
  align-items: center;
  transition: 0.5s;
}

.benefit-card:hover {
  transform: scale(1.1);
  background-color: black;
  color: white;
}

#benefit-description {
  color: #6f6f73;
}



</style>
