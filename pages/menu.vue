<template>
  <div class="flex min-h-[94vh] flex-col justify-between">
    <div
      class="mt-[24px] flex flex-wrap items-center justify-center gap-x-[12px] gap-y-[24px] bg-[#EBECF4] px-[12px] pb-[36px] lg:px-[24px]"
    >
      <Card
        v-for="(dessert, index) in desserts"
        :key="index"
        :dessert-name="dessert.name"
        :cost="dessert.cost"
      />
    </div>

    <Footer></Footer>
  </div>
</template>

<script setup>
import desserts from "../desserts.json";
</script>
