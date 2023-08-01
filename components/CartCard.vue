<template>
  <div
    class="flex h-[72px] w-full overflow-hidden rounded-[5px] border-[3px] border-black bg-[#D9C0DD] lg:h-[90px]"
  >
    <img
      :src="`/${dessertName}.jpg`"
      class="w-[50%] border-r-[3px] border-black object-cover"
    />

    <div class="flex h-full w-[60%] flex-col items-center justify-center">
      <div class="flex w-full items-center justify-between px-[8px]">
        <p class="text-[20px]">{{ dessertName.toUpperCase() }}</p>
        <X
          @click="$emit('deleteFromCart', dessertName)"
          color="#E70000"
          class="h-[24px] w-[24px] cursor-pointer"
        />
      </div>
      <div class="-mt-[4px] flex w-full items-center justify-between px-[8px]">
        <p class="text-[20px] font-black">{{ cost }} ₽</p>
        <NuxtLink :to="`/${dessertName}`">
          <MoveRight color="black" class="h-[24px] w-[24px] cursor-pointer" />
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<script setup>
import { MoveRight, X } from "lucide-vue-next";

const props = defineProps(["dessertName", "cost"]);
const { dessertName, cost } = props;
</script>
