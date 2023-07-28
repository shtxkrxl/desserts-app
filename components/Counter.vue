<template>
  <div class="flex h-[40px] w-[152px] border-[3px] border-black font-bold">
    <button
      @click="$emit('decrease')"
      class="flex flex-1 items-center justify-center border-r-[3px] border-black bg-[#B1A2CD] text-[36px]"
    >
      -
    </button>
    <p
      class="flex flex-1 items-center justify-center text-center text-[32px] font-black"
    >
      {{ props.value }}
    </p>
    <button
      @click="$emit('increase')"
      class="flex flex-1 items-center justify-center border-l-[3px] border-black bg-[#B1A2CD] text-center text-[36px]"
    >
      +
    </button>
  </div>
</template>

<script setup>
const props = defineProps(["value"]);
</script>
