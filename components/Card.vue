<template>
  <NuxtLink :to="`/${dessertName}`">
    <div
      class="h-[264px] w-[45vw] cursor-pointer rounded-[5px] border-[3px] border-black bg-[#D9C0DD] transition-all hover:scale-[1.05] lg:w-[25vw]"
    >
      <img
        :src="`/${dessertName}.jpg`"
        class="h-[70%] w-full border-b-[3px] border-black object-cover"
      />
      <p class="pl-[8px] pt-[8px] text-[22px]">
        {{ dessertName.toUpperCase() }}
      </p>
      <div class="flex w-full items-center justify-between px-[8px]">
        <p class="text-[20px] font-bold">{{ cost }} ₽</p>
        <MoveRight color="black" class="h-[28px] w-[28px]" />
      </div>
    </div>
  </NuxtLink>
</template>

<script setup>
import { MoveRight } from "lucide-vue-next";

const props = defineProps(["dessertName", "cost"]);
const { dessertName, cost } = props;
</script>
