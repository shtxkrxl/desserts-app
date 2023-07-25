<template>
  <div
    class="flex items-center justify-between border-b-[3px] border-black bg-[#B1A2CD] px-[12px] py-[8px]"
  >
    <NuxtLink to="/" class="transition-all active:scale-[1.1]">
      <Dessert color="#7F4988" size="40" />
    </NuxtLink>
    <div class="flex gap-[16px]">
      <NuxtLink to="/" class="transition-all active:scale-[1.1]">
        <MenuSquare color="#7F4988" size="40" />
      </NuxtLink>
      <NuxtLink to="/" class="transition-all active:scale-[1.1]">
        <ShoppingBasket color="#7F4988" size="40" />
      </NuxtLink>
    </div>
  </div>
</template>

<script setup>
import { Dessert, MenuSquare, ShoppingBasket } from "lucide-vue-next";
</script>
