<template>
  <footer
    class="mx-auto flex w-full flex-col items-center border-t-[3px] border-black bg-[#D9C0DD] px-[12px] py-[20px] text-[19px] md:flex-row md:justify-between lg:px-[24px]"
  >
    <div>© Alexandr Kalmaev</div>
    <a
      target="_blank"
      href="https://github.com/shtxkrxl/desserts-app"
      class="flex cursor-pointer items-center"
    >
      <Github color="black" class="h-[25px] w-[25px]" />
      GitHub
    </a>
  </footer>
</template>

<script setup>
import { Github } from "lucide-vue-next";
</script>
