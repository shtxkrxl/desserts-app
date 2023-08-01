<template>
  <div
    class="flex h-[6%] items-center justify-between border-b-[3px] border-black bg-[#B1A2CD] px-[12px] md:px-[24px]"
  >
    <NuxtLink
      to="/"
      class="flex items-center gap-[8px] transition-all active:scale-[1.1]"
    >
      <Dessert color="#7F4988" class="h-[30px] w-[30px]" />
      <p class="hidden text-[20px] font-semibold text-[#7F4988] md:inline">
        DESSERTS
      </p>
    </NuxtLink>
    <div class="flex gap-[16px]">
      <NuxtLink to="/menu" class="transition-all active:scale-[1.1]">
        <MenuSquare color="#7F4988" class="h-[30px] w-[30px]" />
      </NuxtLink>
      <NuxtLink to="/cart" class="transition-all active:scale-[1.1]">
        <ShoppingBasket color="#7F4988" class="h-[30px] w-[30px]" />
      </NuxtLink>
    </div>
  </div>
</template>

<script setup>
import { Dessert, MenuSquare, ShoppingBasket } from "lucide-vue-next";
</script>
