<script setup>
</script>

<template>
    <div class="min-h-screen bg-pink-50 p-8 flex items-center justify-center">
      <div class="max-w-6xl w-full grid grid-cols-1 md:grid-cols-2 gap-8 rounded-3xl overflow-hidden">
        <!-- Left Content Section -->
        <div class="bg-pink-100 p-8 rounded-3xl flex flex-col justify-center items-start space-y-6">
          <h1 class="text-4xl md:text-5xl font-bold text-red-500 leading-tight">
            VERLEIHEN SIE IHREN EVENTS ELEGANZ
          </h1>
          <p class="text-gray-700 text-lg">
            Entdecken Sie die Kunst der perfekten Dekoration. Stöbern Sie in meiner Kollektion und verwandeln Sie Ihre Momente mühelos.
          </p>
          <button class="bg-red-500 hover:bg-red-600 text-white font-semibold py-4 px-8 rounded-full text-lg transition-colors duration-300">
            Kontakt
          </button>
        </div>
  
        <!-- Right Image Section -->
        <div class="relative h-[500px] bg-white rounded-3xl overflow-hidden">
          <div class="absolute inset-0 flex items-center justify-center">
            <div class="w-full h-full relative">
              <!-- Placeholder for the yoga image -->
              <div class="absolute inset-0 bg-gray-100">
                <img 
                  src="../../public/ProfilePicture.JPG"
                  alt="Yoga pose" 
                  class="w-full h-full object-cover"
                />
              </div>
              <!-- Decorative elements -->
              <div class="absolute top-4 right-4">
                <div class="w-4 h-4 bg-red-400 rounded-full"></div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>