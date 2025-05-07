<template>
  <h1>خوش آمدید! لطفا سفارش خود را ثبت نمایید</h1>
  <div class="menu">
    <div class="col">
      <img src="./assets/img/1.jfif" alt="image1" />
      <p>
        <span>قیمت : 1000</span>
        <br />
        <button @click="food.burger++" class="increase">+</button>
        <span class="nums">{{ food.burger }}</span>
        <button
          @click="food.burger--"
          :disabled="food.burger === 0"
          class="decrease"
        >
          -
        </button>
      </p>
    </div>
    <div class="col">
      <img src="./assets/img/2.jfif" alt="image1" />
      <p>
        <span>قیمت : 2000</span>
        <br />
        <button @click="food.hotdog++" class="increase">+</button>
        <span class="nums">{{ food.hotdog }}</span>
        <button
          @click="food.hotdog--"
          :disabled="food.hotdog === 0"
          class="decrease"
        >
          -
        </button>
      </p>
    </div>
    <div class="col">
      <img src="./assets/img/3.jpg" alt="image1" />
      <p>
        <span>قیمت : 1500</span>
        <br />
        <button @click="food.salad++" class="increase">+</button>
        <span class="nums">{{ food.salad }}</span>
        <button
          @click="food.salad--"
          :disabled="food.salad === 0"
          class="decrease"
        >
          -
        </button>
      </p>
    </div>
    <div class="col">
      <img src="./assets/img/4.jpg" alt="image1" />
      <p>
        <span>قیمت : 3000</span>
        <br />
        <button @click="food.chiken++" class="increase">+</button>
        <span class="nums">{{ food.chiken }}</span>
        <button
          @click="food.chiken--"
          :disabled="food.chiken === 0"
          class="decrease"
        >
          -
        </button>
      </p>
    </div>
    <div class="col">
      <img src="./assets/img/5.jfif" alt="image1" />
      <p>
        <span>قیمت : 4000</span>
        <br />
        <button @click="food.pizza++" class="increase">+</button>
        <span class="nums">{{ food.pizza }}</span>
        <button
          @click="food.pizza--"
          :disabled="food.pizza === 0"
          class="decrease"
        >
          -
        </button>
      </p>
    </div>
    <div class="col">
      <img src="./assets/img/6.jpg" alt="image1" />
      <p>
        <span>قیمت : 500</span>
        <br />
        <button @click="food.frenchfries++" class="increase">+</button>
        <span class="nums">{{ food.frenchfries }}</span>
        <button
          @click="food.frenchfries--"
          :disabled="food.frenchfries === 0"
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
  <p v-if="result">
    جمع کل هزینه ها
    <br>
    {{ result }}
  </p>
</template>
<script setup>
import { ref, reactive, computed } from "vue";

const food = reactive({
  burger: 0,
  pizza: 0,
  salad: 0,
  hotdog: 0,
  chiken: 0,
  frenchfries: 0,
});
const result = ref(0);
const order = computed(() => {
  result.value = (food.burger*1000) + (food.pizza*4000) + (food.salad*1500) + (food.hotdog*2000) + (food.chiken*3000) + (food.frenchfries*500);
  return result; 
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
</style>
