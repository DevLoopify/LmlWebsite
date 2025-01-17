<script setup>
import { ref } from 'vue'

const isOpen = ref(false)

const scrollToSection = (sectionId) => {
  const section = document.getElementById(sectionId);
  if (section) {
    section.scrollIntoView({ behavior: 'smooth' });
  }
}
</script>

<template>
    <nav class="bg-white shadow-sm fixed top-0 left-0 w-full z-50">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex justify-between h-20">
          <!-- Logo Section -->
          <div class="flex items-center">
            <div class="flex-shrink-0 flex items-center">
              <span class="text-2xl font-bold text-red-500">Leih mit Liebe</span>
              <div class="ml-2 w-3 h-3 bg-red-400 rounded-full"></div>
            </div>
          </div>
  
          <!-- Navigation Links - Desktop -->
          <div class="hidden md:flex items-center space-x-8">
            <a href="#" @click.prevent="scrollToSection('start')" class="text-gray-700 hover:text-red-500 transition-colors duration-200">Start</a>
            <a href="#" @click.prevent="scrollToSection('services')" class="text-gray-700 hover:text-red-500 transition-colors duration-200">Service</a>
            <a href="#" class="text-gray-700 hover:text-red-500 transition-colors duration-200">Kollektion</a>
            <a href="#" class="text-gray-700 hover:text-red-500 transition-colors duration-200">Über mich</a>
            <button class="bg-red-500 text-white px-6 py-2 rounded-full hover:bg-red-600 transition-colors duration-200">
              Kontakt
            </button>
          </div>
  
          <!-- Mobile Menu Button -->
          <div class="md:hidden flex items-center">
            <button 
              @click="isOpen = !isOpen"
              class="text-gray-700 hover:text-red-500 focus:outline-none"
            >
              <svg 
                class="h-6 w-6" 
                :class="{'hidden': isOpen, 'block': !isOpen }"
                fill="none" 
                viewBox="0 0 24 24" 
                stroke="currentColor"
              >
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
              </svg>
              <svg 
                class="h-6 w-6" 
                :class="{'block': isOpen, 'hidden': !isOpen }"
                fill="none" 
                viewBox="0 0 24 24" 
                stroke="currentColor"
              >
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
              </svg>
            </button>
          </div>
        </div>
      </div>
  
      <!-- Mobile Menu -->
      <div 
        :class="{'block': isOpen, 'hidden': !isOpen}" 
        class="md:hidden"
      >
        <div class="px-2 pt-2 pb-3 space-y-1 sm:px-3">
          <a href="#" class="block px-3 py-2 rounded-md text-gray-700 hover:text-red-500 hover:bg-pink-50 transition-colors duration-200">Start</a>
          <a href="#" class="block px-3 py-2 rounded-md text-gray-700 hover:text-red-500 hover:bg-pink-50 transition-colors duration-200">Service</a>
          <a href="#" class="block px-3 py-2 rounded-md text-gray-700 hover:text-red-500 hover:bg-pink-50 transition-colors duration-200">Kollektion</a>
          <a href="#" class="block px-3 py-2 rounded-md text-gray-700 hover:text-red-500 hover:bg-pink-50 transition-colors duration-200">Über mich</a>
          <button class="mt-4 w-full bg-red-500 text-white px-6 py-2 rounded-full hover:bg-red-600 transition-colors duration-200">
            Kontakt
          </button>
        </div>
      </div>
    </nav>
  </template>
