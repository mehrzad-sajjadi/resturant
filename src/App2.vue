<template>
  <h1>خوش آمدید! لطفا سفارش خود را ثبت نمایید</h1>
  <div class="menu">
    <!-- burger -->
    <div class="col">
      <img src="./assets/img/1.jfif" />
      <p>
        <span>قیمت اصلی : {{food.burger.main_price}}</span>
        <br />
        <span v-if="food.burger.off">{{food.burger.off}} % Off</span>
        <br />
        <button @click="food.burger.count++" class="increase">+</button>
        <span  class="nums">{{ food.burger.count }}</span>
        <button
          @click="food.burger.count--"
          :disabled="food.burger.count === 0"
          class="decrease"
        >
          -
        </button>
      </p>
    </div> 
    <!-- hotdog -->
    <div class="col">
      <img src="./assets/img/2.jfif" />
      <p>
        <span>قیمت اصلی : {{food.hotdog.main_price}}</span>
        <br />
        <span v-if="food.hotdog.off">{{food.hotdog.off}} % Off</span>
        <br />
        <button @click="food.hotdog.count++" class="increase">+</button>
        <span  class="nums">{{ food.hotdog.count }}</span>
        <button
          @click="food.hotdog.count--"
          :disabled="food.hotdog.count === 0"
          class="decrease"
        >
          -
        </button>
      </p>
    </div>
    <!-- salad -->
    <div class="col">
      <img src="./assets/img/3.jpg"  />
      <p>
        <span>قیمت اصلی : {{food.salad.main_price}}</span>
        <br />
        <span v-if="food.salad.off">{{food.salad.off}} % Off</span>
        <br />
        <button @click="food.salad.count++" class="increase">+</button>
        <span  class="nums">{{ food.salad.count }}</span>
        <button
          @click="food.salad.count--"
          :disabled="food.salad.count === 0"
          class="decrease"
        >
          -
        </button>
      </p>
    </div>
    <!-- chiken -->
    <div class="col">
      <img src="./assets/img/4.jpg" />
      <p>
        <span>قیمت اصلی : {{food.chiken.main_price}}</span>
        <br />
        <span v-if="food.chiken.off">{{food.chiken.off}} % Off</span>
        <br />
        <button @click="food.chiken.count++" class="increase">+</button>
        <span  class="nums">{{ food.chiken.count }}</span>
        <button
          @click="food.chiken.count--"
          :disabled="food.chiken.count === 0"
          class="decrease"
        >
          -
        </button>
      </p>
    </div>
    <!-- pizza -->
    <div class="col">
      <img src="./assets/img/5.jfif"  />
      <p>
        <span>قیمت اصلی : {{food.pizza.main_price}}</span>
        <br />
        <span v-if="food.pizza.off">{{food.pizza.off}} % Off</span>
        <br />
        <button @click="food.pizza.count++" class="increase">+</button>
        <span  class="nums">{{ food.pizza.count }}</span>
        <button
          @click="food.pizza.count--"
          :disabled="food.pizza.count === 0"
          class="decrease"
        >
          -
        </button>
      </p>
    </div>
    <!-- frenchfries -->
    <div class="col">
      <img src="./assets/img/6.jpg" />
      <p>
        <span>قیمت اصلی : {{food.frenchfries.main_price}}</span>
        <br />
        <span v-if="food.frenchfries.off">{{food.frenchfries.off}} % Off</span>
        <br />
        <button @click="food.frenchfries.count++" class="increase">+</button>
        <span  class="nums">{{ food.frenchfries.count }}</span>
        <button
          @click="food.frenchfries.count--"
          :disabled="food.frenchfries.count === 0"
          class="decrease"
        >
          -
        </button>
      </p>
    </div>
  </div>
  <div class="order-wrapper">
    <button @click="order" class="order" type="button">ثبت سفارش</button>
  </div>
  <p class="result" v-if="result">
    <div>
      جمع کل هزینه ها اصلی
      <br>
      {{ result }}  
    </div>
    <div>
      جمع کل هزینه ها با تخفیف
      <br>
      {{ offPrice }}  
    </div>
  </p>
</template>
<script setup>
import { ref, reactive, computed , onBeforeMount } from "vue";

onBeforeMount(()=>{
  alert("به رستوران ما خیلی خوش آمدید");
})

const food = ref({
  burger:{
    count : 0 ,
    main_price : 1000,
    off : 35 
  },
  hotdog:{
    count : 0 ,
    main_price : 2000,
    off : 12  
  },
  salad:{
    count : 0 ,
    main_price : 1500,
    off : 10
  },
  chiken:{
    count : 0 ,
    main_price : 3000,
    off : 0
  },
  pizza:{
    count : 0 ,
    main_price : 4000,
    off : 20
  },
  frenchfries:{
    count : 0 ,
    main_price : 500,
    off : 0
  }
});
const result = ref(0);

const off = reactive({
  burger: (food.value.burger.main_price*(100 - food.value.burger.off))/100,
  hotdog : (food.value.hotdog.main_price*(100 - food.value.hotdog.off))/100,
  pizza: (food.value.pizza.main_price*(100 - food.value.pizza.off))/100,
  salad: (food.value.salad.main_price*(100 - food.value.salad.off))/100,
  chiken: (food.value.chiken.main_price*(100 - food.value.chiken.off))/100,
  frenchfries: (food.value.frenchfries.main_price*(100 - food.value.frenchfries.off))/100 
})

const offPrice = ref(0);
const order = computed(() => {
  result.value = 
    (food.value.burger.count * food.value.burger.main_price) +
    (food.value.pizza.count * food.value.pizza.main_price) +
    (food.value.salad.count * food.value.salad.main_price) +
    (food.value.hotdog.count * food.value.hotdog.main_price) +
    (food.value.chiken.count * food.value.chiken.main_price) +
    (food.value.frenchfries.count * food.value.frenchfries.main_price) 
  ;
  offPrice.value =  
    (food.value.burger.count * off.burger) +
    (food.value.pizza.count * off.pizza) + 
    (food.value.salad.count * off.salad) + 
    (food.value.hotdog.count * off.hotdog) + 
    (food.value.chiken.count * off.chiken) + 
    (food.value.frenchfries.count *  off.frenchfries)
  ;
  return {result,offPrice}; 
});
</script>
<style scoped>
h1 {
    text-align: center;
}
.menu {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
    max-width: 900px;
    margin: 0 auto;
    padding: 20px;
    text-align: center;
}

.col {
    display: flex;
    flex-direction: column;
    align-items: center;
    border-radius: 8px;
}
p {
    text-align: center;
    font-size: 20px;
    font-weight: bold;
}
button {
    border-radius: 30%;
    cursor: pointer;
    border: 1px solid rgb(90, 76, 76);
    color: white;
    font-size: 15px;
    padding: 5px 10px;
}
img {
    width: 200px;
    height: 200px;
    object-fit: cover;
    border-radius: 15px;
}
.decrease {
    background-color: red;
}
.increase {
    background-color: rgb(0, 255, 30);
}
.nums {
    margin: 0 10px;
}
.order-wrapper{
    display: flex;
    justify-content: center;
  
}
.order {
    width: 60%;
    border-radius: 7px;
    color: black;
    background-color: yellow;
    justify-content: center;
    align-items: center;
    margin: auto;
}
.result{
  display: flex;
  justify-content:space-around ;
  width: 50%;
  margin: auto;
}
</style>
