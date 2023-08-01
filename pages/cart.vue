<template>
  <div class="flex min-h-[94vh] flex-col justify-between bg-[#EBECF4]">
    <Head>
      <title>Cart</title>
    </Head>
    <p
      class="text-outline-black px-[12px] text-[48px] font-black text-[#B1A2CD] lg:px-[24px]"
    >
      КОРЗИНА
    </p>
    <div
      class="flex w-full flex-col gap-[8px] px-[12px] pb-[24px] lg:flex-row lg:flex-wrap lg:gap-x-[36px] lg:gap-y-[24px] lg:px-[24px]"
    >
      <div
        v-if="cartOnPage.length !== 0"
        v-for="dessert in cartOnPage.sort((a, b) => {
          return b.cost - a.cost;
        })"
        :key="dessert.name"
        class="flex w-full flex-col gap-[8px] lg:w-[45%]"
      >
        <CartCard
          @delete-from-cart="deleteFromCart"
          :dessert-name="dessert.name"
          :cost="dessert.cost"
        />
        <div class="flex w-full items-center justify-between">
          <Counter
            :value="dessert.count"
            @increase="increase(dessert.name)"
            @decrease="decrease(dessert.name)"
          />
          <p class="text-outline-black text-[32px] font-black text-[#B1A2CD]">
            {{ dessert.count * dessert.cost }} ₽
          </p>
        </div>
      </div>
    </div>

    <div
      class="flex flex-col items-center justify-center gap-[8px] border-t-[3px] border-black bg-[#D9C0DD] pb-[16px] pt-[8px]"
    >
      <p class="text-[36px]">
        ИТОГО:
        <span class="text-outline-black text-[36px] font-black text-white"
          >{{ sum }} ₽</span
        >
      </p>
      <button
        class="rounded-[5px] border-[3px] border-black bg-[#EBECF4] px-[24px] py-[4px] text-[20px]"
      >
        Продолжить
      </button>
    </div>
  </div>
</template>

<script setup>
const cartOnPage = ref([]);
const sum = ref(0);

onMounted(() => {
  cartOnPage.value = JSON.parse(localStorage.getItem("cart"));
  calcSum();
});

const increase = (dessertName) => {
  const array = [];
  const cart = JSON.parse(localStorage.getItem("cart"));
  const count = ref(1);
  const cost = ref(1);

  for (let i = 0; i < cart.length; i++) {
    if (cart[i].name === dessertName) {
      if (cart[i].count < 99) {
        count.value = cart[i].count + 1;
      } else {
        count.value = cart[i].count;
      }
      cost.value = cart[i].cost;
    } else {
      array.push(cart[i]);
    }
  }
  array.push({
    name: dessertName,
    count: count.value,
    cost: cost.value,
  });
  localStorage.setItem("cart", JSON.stringify(array));
  cartOnPage.value = JSON.parse(localStorage.getItem("cart"));
  calcSum();
};

const decrease = (dessertName) => {
  const array = [];
  const cart = JSON.parse(localStorage.getItem("cart"));
  const count = ref(1);
  const cost = ref(1);

  for (let i = 0; i < cart.length; i++) {
    if (cart[i].name === dessertName) {
      if (cart[i].count > 1) {
        count.value = cart[i].count - 1;
      } else {
        count.value = cart[i].count;
      }
      cost.value = cart[i].cost;
    } else {
      array.push(cart[i]);
    }
  }
  array.push({
    name: dessertName,
    count: count.value,
    cost: cost.value,
  });
  localStorage.setItem("cart", JSON.stringify(array));
  cartOnPage.value = JSON.parse(localStorage.getItem("cart"));
  calcSum();
};

const deleteFromCart = (dessertName) => {
  const array = [];
  cartOnPage.value = JSON.parse(localStorage.getItem("cart"));

  if (cartOnPage.value) {
    for (let i = 0; i < cartOnPage.value.length; i++) {
      if (cartOnPage.value[i].name === dessertName) {
        continue;
      } else {
        array.push(cartOnPage.value[i]);
      }
    }
    localStorage.setItem("cart", JSON.stringify(array));
  }
  cartOnPage.value = JSON.parse(localStorage.getItem("cart"));
  calcSum();
};

const calcSum = () => {
  const cart = JSON.parse(localStorage.getItem("cart"));
  let result = 0;
  if (cart.length !== 0) {
    for (let i = 0; i < cart.length; i++) {
      result += cart[i].cost * cart[i].count;
    }
  }
  sum.value = result;
};
</script>

<style>
.text-outline-black {
  -webkit-text-stroke: 2px black;
}
</style>
