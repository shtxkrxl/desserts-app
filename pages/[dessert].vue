<template>
  <div class="flex min-h-[94vh] flex-col justify-between">
    <Head>
      <title>{{ dessertName.toUpperCase() }}</title>
    </Head>
    <div
      class="mt-[24px] flex flex-col gap-[8px] bg-[#EBECF4] px-[12px] lg:flex-row lg:gap-[24px] lg:px-[24px]"
    >
      <div
        class="relative h-[472px] overflow-hidden rounded-[10px] border-[3px] border-black lg:mb-[24px] lg:h-[700px] lg:w-[70%]"
      >
        <img
          :src="`/${dessertName}.jpg`"
          class="pointer-events-none h-full w-full object-cover"
        />
        <p
          class="text-outline absolute left-0 top-[87%] px-[12px] text-[40px] font-black tracking-[1px] text-[#B1A2CD]/90 lg:top-[85%] lg:text-[70px] lg:tracking-[3px]"
        >
          {{ dessertName.toUpperCase() }}
        </p>
      </div>

      <div class="flex flex-col gap-[16px] lg:w-[30%]">
        <div class="flex items-center justify-between">
          <p
            class="text-outline-black text-[48px] font-black tracking-[1px] text-[#B1A2CD]"
          >
            {{ cost }} ₽
          </p>
          <Counter :value="count" @increase="increase" @decrease="decrease" />
        </div>

        <button
          @click="addToCart"
          v-if="!inCart"
          class="mb-[8px] w-full border-[3px] border-black bg-[#B1A2CD] py-[4px] text-[24px] lg:px-[16px]"
        >
          Добавить в корзину
        </button>

        <button
          @click="deleteFromCart"
          v-if="inCart"
          class="mb-[8px] w-full border-[3px] border-black bg-[#E37070] py-[4px] text-[24px] lg:px-[16px]"
        >
          Удалить из корзины
        </button>

        <p class="pb-[8px] text-[26px]">{{ description }}</p>

        <div
          class="border-t-[3px] border-black pb-[24px] pt-[16px] text-[24px]"
        >
          <div class="flex items-center justify-between">
            <p>Вес</p>
            <p>{{ weight }} г.</p>
          </div>
          <div class="flex items-center justify-between">
            <p>Порций</p>
            <p>{{ portion }}</p>
          </div>
          <div class="flex items-center justify-between">
            <p>Белки</p>
            <p>{{ protein }}</p>
          </div>
          <div class="flex items-center justify-between">
            <p>Жиры</p>
            <p>{{ fats }}</p>
          </div>
          <div class="flex items-center justify-between">
            <p>Углеводы</p>
            <p>{{ carbohydrates }}</p>
          </div>
          <div class="flex items-center justify-between">
            <p>Каллорийность</p>
            <p>{{ calorific }}</p>
          </div>
        </div>
      </div>
    </div>

    <Footer></Footer>
  </div>
</template>

<script setup>
import desserts from "../desserts.json";

const route = useRoute();

const dessertName = route.params.dessert;
const {
  portion,
  weight,
  cost,
  description,
  protein,
  fats,
  carbohydrates,
  calorific,
} = desserts[dessertName];

const count = ref(1);
const inCart = ref(false);

onMounted(() => {
  const cart = JSON.parse(localStorage.getItem("cart"));

  if (cart) {
    for (let i = 0; i < cart.length; i++) {
      if (cart[i].name === dessertName) {
        count.value = cart[i].count;
        inCart.value = true;
      }
    }
  }
});

const increase = () => {
  if (count.value < 99) {
    count.value += 1;
  }
  if (inCart.value) {
    addToCart();
  }
};
const decrease = () => {
  if (count.value > 1) {
    count.value -= 1;
  }
  if (inCart.value) {
    addToCart();
  }
};

const addToCart = () => {
  const array = [];
  const cart = JSON.parse(localStorage.getItem("cart"));

  if (cart) {
    for (let i = 0; i < cart.length; i++) {
      if (cart[i].name === dessertName) {
        continue;
      } else {
        array.push(cart[i]);
      }
    }
    array.push({ name: dessertName, count: count.value, cost });
    localStorage.setItem("cart", JSON.stringify(array));
  } else {
    array.push({ name: dessertName, count: count.value, cost });
    localStorage.setItem("cart", JSON.stringify(array));
  }

  inCart.value = true;
};

const deleteFromCart = () => {
  const array = [];
  const cart = JSON.parse(localStorage.getItem("cart"));

  if (cart) {
    for (let i = 0; i < cart.length; i++) {
      if (cart[i].name === dessertName) {
        continue;
      } else {
        array.push(cart[i]);
      }
    }
    localStorage.setItem("cart", JSON.stringify(array));
  }

  count.value = 1;
  inCart.value = false;
};
</script>

<style>
.text-outline {
  -webkit-text-stroke: 1px white;
}
.text-outline-black {
  -webkit-text-stroke: 2px black;
}
@media (min-width: 1024px) {
  .text-outline {
    -webkit-text-stroke: 2px white;
  }
}
</style>
