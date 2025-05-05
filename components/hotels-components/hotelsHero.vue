<script setup lang="ts">

</script>

<template>
  <div>
    <!-- Hero Image Section -->
    <div class="absolute h-[537px] w-full">
      <img src="/images/hotels-hero-banner.jpg" alt="Hotels Banner" class="object-cover object-center w-full h-full">
      <div class="absolute inset-0 bg-black/20"></div>
    </div>

    <!-- Content Section -->
    <div class="relative z-10 px-4 sm:px-6 xl:px-[104px] py-16 text-white">
      <!-- Text Content -->
      <div class="max-w-[440px]">
        <h1 class="mb-4 text-3xl font-700 md:text-[45px] leading-10">
          Make your travel wishlist, we'll do the rest
        </h1>
        <p class="text-xl font-500">
          Special offers to suit your plan
        </p>
      </div>

      <!-- Search Form -->
      <div
        class="relative w-[90%] md:w-full md:max-w-[1232px] mx-auto md:absolute md:-translate-x-1/2 md:bottom-[-300px] md:left-1/2 z-20 mt-8 md:mt-0 shadow-lg">
        <div class="bg-white rounded-lg">
          <!-- Form Content -->
          <div class="p-4 space-y-4 md:p-6 md:space-y-5">
            <p class="text-[#414d41] text-xl font-600">Where are you staying?</p>
            <!-- Grid on mobile, flex row on desktop -->
            <div class="grid grid-cols-1 gap-4 md:flex md:flex-row md:items-center md:gap-3">
              <div class="md:flex-1">
                <label class="text-sm text-gray-600">Enter Destination</label>
                <div class="relative mt-1">
                  <input type="text" placeholder="Dubai"
                    class="w-full p-2 text-sm text-gray-900 border rounded-md md:p-3 md:text-base" />
                  <button class="absolute transform -translate-y-1/2 right-3 top-1/2">
                    <icon name="material-symbols:location-on" class="text-gray-900"></icon>
                  </button>
                </div>
              </div>
              <div class="md:flex-1">
                <label class="text-sm text-gray-600">Check in - Check out</label>
                <input type="text" value="07 Nov 22 - 13 Nov 22"
                  class="w-full p-2 mt-1 text-sm text-gray-900 border rounded-md md:p-3 md:text-base" />
              </div>
              <div class="md:flex-1">
                <label class="text-sm text-gray-600">Rooms & Guests</label>
                <input type="text" value="1 Room, 2 Guests"
                  class="w-full p-2 mt-1 text-sm text-gray-900 border rounded-md md:p-3 md:text-base" />
              </div>
            </div>

            <div class="flex items-center justify-end gap-4 mt-4 md:mt-6 text-[#112211]">
              <button class="flex items-center text-xs md:text-sm font-500">
                <icon name="material-symbols:add" class="me-1"></icon>
                Add Promo Code
              </button>
              <button class="search-form-btn">
                <icon name="ri:hotel-line" class="me-1 w-5 h-5"></icon>
               <span class="text-sm">Show Places</span>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>