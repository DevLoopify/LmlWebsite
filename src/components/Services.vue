<template>
    <div class="w-full max-w-6xl mx-auto px-4 py-8 md:py-16">
      <!-- Section Header -->
      <div class="text-center mb-8 md:mb-12">
        <h2 class="text-3xl md:text-4xl font-bold text-red-500 mb-3 md:mb-4">Services</h2>
        <p class="text-gray-600 max-w-2xl mx-auto text-sm md:text-base px-4">
          Entdecke das perfekte Angebot um deine Täume zu verwirklichen.
        </p>
      </div>
  
      <!-- Carousel Container -->
      <div 
        class="relative"
        @touchstart="touchStart"
        @touchmove="touchMove"
        @touchend="touchEnd"
      >
        <!-- Cards Container -->
        <div class="flex justify-center items-center gap-3 md:gap-6">
          <TransitionGroup name="carousel">
            <div
              v-for="(service, index) in visibleServices"
              :key="service.id"
              class="w-full transform transition-all duration-500"
              :class="{
                'max-w-[280px] md:max-w-sm': true,
                'scale-95 md:scale-100': index === 1,
                'hidden md:block': index === 0 || index === 2
              }"
            >
              <div class="bg-white rounded-xl md:rounded-2xl shadow-lg overflow-hidden">
                <div class="aspect-w-16 aspect-h-9">
                  <img
                    :src="service.image"
                    :alt="service.title"
                    class="w-full h-36 md:h-48 object-cover"
                  />
                </div>
                <div class="p-4 md:p-6">
                  <h3 class="text-lg md:text-xl font-semibold text-gray-800 mb-2">
                    {{ service.title }}
                  </h3>
                  <p class="text-sm md:text-base text-gray-600 line-clamp-3 md:line-clamp-none">
                    {{ service.description }}
                  </p>
                  <button class="mt-3 md:mt-4 text-red-500 font-semibold hover:text-red-600 transition-colors duration-200 text-sm md:text-base">
                    Jetzt Buchen
                  </button>
                </div>
              </div>
            </div>
          </TransitionGroup>
        </div>
  
        <!-- Navigation Buttons - Hidden on Mobile -->
        <button
          @click="prevSlide"
          class="hidden md:block absolute left-0 top-1/2 -translate-y-1/2 -translate-x-4 bg-white p-2 rounded-full shadow-lg text-red-500 hover:text-red-600 transition-colors duration-200"
        >
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
          </svg>
        </button>
        <button
          @click="nextSlide"
          class="hidden md:block absolute right-0 top-1/2 -translate-y-1/2 translate-x-4 bg-white p-2 rounded-full shadow-lg text-red-500 hover:text-red-600 transition-colors duration-200"
        >
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
          </svg>
        </button>
      </div>
  
      <!-- Dots Indicator -->
      <div class="flex justify-center space-x-2 mt-6 md:mt-8">
        <button
          v-for="(_, index) in services"
          :key="index"
          @click="activeIndex = index"
          class="w-2 h-2 rounded-full transition-colors duration-200"
          :class="index === activeIndex ? 'bg-red-500' : 'bg-gray-300'"
        />
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, computed } from 'vue'
  
  const services = [
    {
      id: 1,
      title: "Deko-Verleih",
      description: "Lassen Sie sich von meiner Kollektion inspirieren und verleihen Sie Ihren Events Eleganz.",
      image: "../../public/IMG_8114.jpg"
    },
    {
      id: 2,
      title: "Dekorationsservice",
      description: "Lasen Sie sich von mir beraten und verwandeln Sie Ihre Momente mühelos.",
      image: "./../public/IMG_8114.jpg"
    }
  ]
  
  const activeIndex = ref(0)
  const touchStartX = ref(0)
  const touchEndX = ref(0)
  
  const visibleServices = computed(() => {
    const result = []
    for (let i = 0; i < 2; i++) {
      const index = (activeIndex.value + i) % services.length
      result.push(services[index])
    }
    return result
  })
  
  const nextSlide = () => {
    activeIndex.value = (activeIndex.value + 1) % services.length
  }
  
  const prevSlide = () => {
    activeIndex.value = (activeIndex.value - 1 + services.length) % services.length
  }
  
  // Touch handlers for mobile swipe
  const touchStart = (e) => {
    touchStartX.value = e.changedTouches[0].screenX
  }
  
  const touchMove = (e) => {
    touchEndX.value = e.changedTouches[0].screenX
  }
  
  const touchEnd = () => {
    const minSwipeDistance = 50
    const swipeDistance = touchEndX.value - touchStartX.value
    
    if (Math.abs(swipeDistance) > minSwipeDistance) {
      if (swipeDistance > 0) {
        prevSlide()
      } else {
        nextSlide()
      }
    }
  }
  </script>
  
  <style scoped>
  .carousel-enter-active,
  .carousel-leave-active {
    transition: all 0.5s ease;
  }
  
  .carousel-enter-from {
    opacity: 0;
    transform: translateX(100%);
  }
  
  .carousel-leave-to {
    opacity: 0;
    transform: translateX(-100%);
  }
  
  .carousel-leave-active {
    position: absolute;
  }
  
  @media (max-width: 768px) {
    .carousel-enter-from {
      transform: translateX(50%);
    }
    
    .carousel-leave-to {
      transform: translateX(-50%);
    }
  }
  </style>