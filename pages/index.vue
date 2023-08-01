<template>
  <div class="h-[94%] w-full">
    <Swiper class="h-full w-full" navigation loop :modules="modules"
      ><SwiperSlide>
        <div
          class="relative h-full w-full bg-[url('/croissant.jpg')] bg-cover bg-center"
        >
          <div
            class="absolute left-0 top-0 flex h-full w-full items-center justify-center bg-[#B1A2CD]/20"
          >
            <NuxtLink to="/croissant">
              <p
                class="text-outline mb-[100px] cursor-pointer select-none text-[50px] font-black tracking-[5px] text-[#B1A2CD]/90 transition-all hover:scale-[1.1] lg:text-[70px]"
              >
                CROISSANT
              </p>
            </NuxtLink>
          </div>
        </div>
      </SwiperSlide>

      <SwiperSlide
        ><div
          class="relative h-full w-full bg-[url('/cheesecake.jpg')] bg-cover bg-center"
        >
          <div
            class="absolute left-0 top-0 flex h-full w-full items-center justify-center bg-[#B1A2CD]/20"
          >
            <NuxtLink to="/cheesecake">
              <p
                class="text-outline mb-[100px] cursor-pointer select-none text-[43px] font-black tracking-[4px] text-[#B1A2CD]/90 transition-all hover:scale-[1.1] lg:text-[70px]"
              >
                CHEESECAKE
              </p>
            </NuxtLink>
          </div>
        </div></SwiperSlide
      >

      <SwiperSlide
        ><div
          class="relative h-full w-full bg-[url('/tartlet.jpg')] bg-cover bg-center"
        >
          <div
            class="absolute left-0 top-0 flex h-full w-full items-center justify-center bg-[#B1A2CD]/20"
          >
            <NuxtLink to="/tartlet">
              <p
                class="text-outline mb-[100px] cursor-pointer select-none text-[50px] font-black tracking-[5px] text-[#B1A2CD]/90 transition-all hover:scale-[1.1] lg:text-[70px]"
              >
                TARTLET
              </p>
            </NuxtLink>
          </div>
        </div></SwiperSlide
      >
    </Swiper>
  </div>
</template>

<script setup>
import { Swiper, SwiperSlide } from "swiper/vue";
import { Navigation } from "swiper/modules";
import "swiper/css";
import "swiper/css/navigation";

const modules = [Navigation];
</script>

<style>
.text-outline {
  -webkit-text-stroke: 2px white;
}

.swiper-button-prev {
  height: 56px;
  width: 56px;
  border-radius: 100%;
  border-width: 3px;
  border-color: white;
  background-color: #b1a2cdcc;
}
.swiper-button-prev::after {
  content: " ";
  background: url("/move-right.svg") no-repeat center;
  background-size: 32px;
  display: block;
  height: 56px;
  width: 56px;
  border-radius: 100%;
}

.swiper-button-next {
  height: 56px;
  width: 56px;
  border-radius: 100%;
  border-width: 3px;
  border-color: white;
  background-color: #b1a2cdcc;
}
.swiper-button-next::after {
  content: " ";
  background: url("/move-right.svg") no-repeat center;
  rotate: 180deg;
  background-size: 32px;
  display: block;
  height: 56px;
  width: 56px;
  border-radius: 100%;
}

* {
  --swiper-navigation-top-offset: 90%;
  --swiper-navigation-sides-offset: 30px;
  --swiper-navigation-color: transparent;
}

@media (min-width: 768px) {
  * {
    --swiper-navigation-top-offset: 44%;
  }
}
</style>
