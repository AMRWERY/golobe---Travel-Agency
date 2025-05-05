<script setup lang="ts">
const isMobileMenuOpen = ref(false);

// Toggle mobile menu
const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value;
};
</script>

<template>
  <div>
    <div class="relative h-[581px]">
      <!-- Background Image -->
      <div class="absolute inset-0 bg-center bg-cover">
        <img src="/images/home-her-banner.jpg" alt="home-her-banner"
          class=" h-[581px] w-full object-cover object-center">
        <div class="absolute inset-0 bg-black/20"></div>
      </div>

      <!-- Hero Content -->
      <div class="relative z-10 min-h-screen">
        <!-- Navigation -->
        <div class="flex justify-between items-center px-4 sm:px-6 xl:px-[104px] pt-8">
          <!-- Left Navigation -->
          <div class="items-center hidden space-x-6 md:flex">
            <nuxt-link to="/flights" class="flex items-center gap-2 font-500 text-white">
              <icon name="material-symbols:flight-takeoff-rounded" class="w-[22px] h-5"></icon>
              <span>Find Flight</span>
            </nuxt-link>
            <nuxt-link to="/hotels" class="flex items-center gap-2 font-500 text-white">
              <icon name="material-symbols:king-bed-rounded" class="w-[22px] h-5"></icon>
              <span>Find Stays</span>
            </nuxt-link>
          </div>

          <!-- Logo -->
          <div class="md:hidden">
            <nuxt-link to="/">
              <img class="h-[36px] w-[110.35px]" src="@/assets/golobe-logo-light.svg" alt="Mobile Logo">
            </nuxt-link>
          </div>

          <!-- Mobile Menu Button -->
          <div class="flex md:hidden">
            <button @click="toggleMobileMenu" class="text-white rounded-md focus:outline-none">
              <icon name="tabler:menu-deep"></icon>
            </button>
          </div>

          <div class="absolute hidden transform -translate-x-1/2 left-1/2 top-8 md:flex">
            <nuxt-link to="/">
              <img class="h-[36px] w-[110.35px]" src="@/assets/golobe-logo-light.svg" alt="Logo">
            </nuxt-link>
          </div>

          <!-- Right Navigation -->
          <div class="items-center hidden space-x-6 md:flex">
            <nuxt-link to="" class="font-500 text-white">Login</nuxt-link>
            <nuxt-link to="" class="px-6 py-2 font-500 text-black bg-white rounded-md">Sign up</nuxt-link>
            <!-- display only if user is auth -->
            <div class="flex items-center justify-center">
              <nuxt-link to="/favourites" class="flex items-center">
                <icon name="heroicons-outline:heart" class="text-white w-4 h-[18px]"></icon>
                <p class="text-sm font-600 ms-1 text-white">Favourites</p>
              </nuxt-link>
              <div class="mx-4 h-5 w-0.5 bg-gray-300 text-white"></div>
              <div class="relative">
                <!-- user-dropdown-menu component -->
                <user-dropdown-menu :is-light="true" />
              </div>
            </div>
          </div>
        </div>

        <!-- Mobile Menu Dropdown -->
        <transition enter-active-class="transition-all duration-300 ease-out"
          leave-active-class="transition-all duration-200 ease-in" enter-from-class="opacity-0 max-h-0"
          enter-to-class="opacity-100 max-h-64" leave-from-class="opacity-100 max-h-64"
          leave-to-class="opacity-0 max-h-0">
          <div v-show="isMobileMenuOpen"
            class="absolute left-0 z-50 w-full overflow-hidden bg-white bg-opacity-75 md:hidden top-20">
            <div class="pt-2 pb-3 space-y-1">
              <nuxt-link to="/flights"
                class="flex items-center gap-1 px-3 py-2 text-gray-700 hover:bg-gray-50 hover:bg-opacity-80">
                <icon name="material-symbols:flight-takeoff-rounded" class="w-[22px] h-5"></icon>
                <span class="text-sm capitalize font-600">find flight</span>
              </nuxt-link>
              <nuxt-link to="/hotels"
                class="flex items-center gap-1 px-3 py-2 text-gray-700 hover:bg-gray-50 hover:bg-opacity-80">
                <icon name="material-symbols:king-bed-rounded" class="w-[22px] h-5"></icon>
                <span class="text-sm capitalize font-600">find stays</span>
              </nuxt-link>
              <nuxt-link to=""
                class="flex items-center gap-1 px-3 py-2 text-gray-700 hover:bg-gray-50 hover:bg-opacity-80">
                <icon name="material-symbols:login" class="w-[22px] h-5"></icon>
                <span class="text-sm capitalize font-600">login</span>
              </nuxt-link>
              <nuxt-link to=""
                class="flex items-center gap-1 px-3 py-2 text-gray-700 hover:bg-gray-50 hover:bg-opacity-80">
                <icon name="mdi:account-plus" class="w-[22px] h-5"></icon>
                <span class="text-sm capitalize font-600">sign up</span>
              </nuxt-link>
              <!-- display only if user is auth -->
              <div class="flex items-center px-3 py-2 text-gray-700 hover:bg-gray-50">
                <nuxt-link to="/favourites" role="button" class="flex items-center">
                  <icon name="heroicons-outline:heart" class="w-[22px] h-5"></icon>
                  <p class="text-sm font-600 ms-1">Favourites</p>
                </nuxt-link>
              </div>
              <div class="px-3 py-2">
                <!-- user-dropdown-menu component -->
                <user-dropdown-menu :is-mobile="true" />
              </div>
            </div>
          </div>
        </transition>

        <!-- Hero Text -->
        <div
          class="flex flex-col items-center justify-center px-4 pt-32 text-center text-white md:pt-0 md:min-h-[80vh] mx-auto">
          <p class="text-2xl font-700 text-[45px]">Helping Others</p>
          <h1 class="mt-1 text-6xl uppercase font-700 sm:text-8xl">live & travel</h1>
          <p class="mt-4 mb-16 text-xl font-600">Special offers to suit your plan</p>
        </div>

        <!-- Search Form - Absolute positioning on desktop, relative on mobile -->
        <div
          class="relative w-[90%] mx-auto md:absolute md:w-full md:max-w-[1232px] md:transform md:-translate-x-1/2 bg-white rounded-lg overflow-hidden md:left-1/2 md:bottom-[-50px] z-20 mt-8 md:mt-0 shadow-lg">
          <!-- Tabs -->
          <div class="flex justify-start border-b border-gray-100">
            <div class="relative px-6 py-5">
              <button class="flex items-center text-center text-color font-500">
                <icon name="material-symbols:flight" class="me-2 h-5 w-[22px]"></icon>
                Flights
              </button>
              <div class="absolute bottom-0 start-6 end-6 h-[3px] bg-[#8DD3BB]"></div>
            </div>
            <div class="h-10 w-[2px] mx-2 my-auto bg-gray-200"></div>
            <button class="flex items-center px-6 py-5 text-color font-500">
              <icon name="material-symbols:king-bed" class="me-2 h-5 w-[22px]"></icon>
              Stays
            </button>
          </div>
          <!-- Form fields -->
          <div class="p-4 space-y-4 md:p-6 md:space-y-6">
            <div class="grid grid-cols-1 gap-4 md:flex md:flex-row md:items-center md:gap-3">
              <div class="md:flex-1">
                <label class="text-sm text-color">From - To</label>
                <div class="relative mt-1">
                  <input type="text" value="Lahore - Karachi"
                    class="w-full p-2 text-sm border rounded-md md:p-3 md:text-base" />
                  <button class="absolute transform -translate-y-1/2 right-3 top-1/2">
                    <icon name="mdi:exchange" class="w-[15px] h-5"></icon>
                  </button>
                </div>
              </div>
              <div class="md:flex-1">
                <label class="text-sm text-color">Trip</label>
                <select class="w-full p-2 mt-1 text-sm bg-white border rounded-md appearance-none md:p-3 md:text-base">
                  <option>Return</option>
                  <option>One Way</option>
                </select>
              </div>
              <div class="md:flex-1">
                <label class="text-sm text-color">Depart - Return</label>
                <input type="text" value="07 Nov 22 - 13 Nov 22"
                  class="w-full p-2 mt-1 text-sm border rounded-md md:p-3 md:text-base" />
              </div>
              <div class="md:flex-1">
                <label class="text-sm text-color">Passenger - Class</label>
                <input type="text" value="1 Passenger, Economy"
                  class="w-full p-2 mt-1 text-sm border rounded-md md:p-3 md:text-base" />
              </div>
            </div>

            <div class="flex items-center justify-end gap-4 mt-4 md:mt-6">
              <button class="flex items-center text-xs md:text-sm font-500">
                <icon name="material-symbols:add" class="me-1 w-[15px] h-[15px]"></icon>
                Add Promo Code
              </button>
              <button class="search-form-btn">
                <icon name="tabler:send" class="me-1 w-3.5 h-3.5"></icon>
                Show Flights
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>