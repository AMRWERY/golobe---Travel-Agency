<script setup lang="ts">
interface User {
  name: string
  img: string,
  rate: string,
  desc: string,
}

const users: User[] = [
  { name: 'Ralph Waldo', img: 'https://justfields.com/storage/projects/7M5rV059/user-01.jpg', rate: '5.0 Amazing', desc: "It is easy in the world to live after the world's opinion; it is easy in solitude to live after our own; but the great man is he who in the midst of the crowd keeps with perfect sweetness the independence of solitude." },
  { name: 'Lemony Snicket', img: 'https://justfields.com/storage/projects/7M5rV059/user-02.jpg', rate: '4.9 Amazing', desc: "Friends can make you feel that the world is smaller and less sneaky than it really is, because you know people who have similar experiences." },
  { name: 'C.S. Lewis', img: 'https://justfields.com/storage/projects/7M5rV059/user-03.jpg', rate: '4.8 Amazing', desc: "Wrong will be right, when Aslan comes in sight, At the sound of his roar, sorrows will be no more, When he bares his teeth, winter meets its death, And when he shakes his mane, we shall have spring again." },
  { name: 'Gene Stratton', img: 'https://justfields.com/storage/projects/7M5rV059/user-04.jpg', rate: '4.7 Amazing', desc: "If you are lazy, and accept your lot, you may live in it. If you are willing to work, you can write your name anywhere you choose." },
  { name: 'Rachel Naomi', img: 'https://justfields.com/storage/projects/7M5rV059/user-05.jpg', rate: '4.6 Amazing', desc: "The most basic and powerful way to connect to another person is to listen. Just listen. Perhaps the most important thing we ever give each other is our attention…. A loving silence often has far more power to heal and to connect than the most well-intentioned words." },
]
</script>

<template>
  <div>
    <div class="mx-auto md:w-full md:max-w-[1232px] px-4 md:px-0">
      <div class="mt-6 mb-4 md:mb-8 md:mt-12">
        <!-- breadcrumb component -->
        <breadcrumb />
      </div>

      <div class="flex flex-col md:flex-row justify-between items-start gap-4">
        <div class="flex-1 w-full">
          <div class="flex justify-between items-center w-full md:block">
            <div class="flex items-center justify-start">
              <p class="text-2xl font-700 text-gray-800">CVK Park Bosphorus Hotel Istanbul</p>
              <div class="flex items-center gap-2 ms-[16.5px]">
                <div class="flex items-center justify-center text-[#FF8682] -space-x-1">
                  <icon name="material-symbols:star-rate" class="w-4 h-4" v-for="n in 5" :key="n" />
                </div>
                <span class="text-xs font-500">5 Star Hotel</span>
              </div>
            </div>
            <!-- Mobile Price -->
            <p class="md:hidden text-3xl font-700 text-[#FF8682] flex items-center justify-center">$240<span
                class="text-lg mt-2">/night</span></p>
          </div>
          <p class="text-sm font-500 flex items-center text-gray-600 mt-4 mb-2">
            <icon name="material-symbols-light:location-on-rounded" class="me-2 w-4 h-5"></icon>
            Gümüssuyu Mah. Inönü Cad. No:8, Istanbul 34437
          </p>
          <div class="flex items-center gap-4">
            <div class="border border-[#cdece1] px-2 py-1 rounded-md">
              <span class="text-xs text-[#6a756a]">4.2</span>
            </div>
            <p class="text-base font-700 text-gray-800">
              Very Good <span class="font-400">54 reviews</span>
            </p>
          </div>
        </div>

        <div class="w-full md:w-auto">
          <div class="flex flex-col items-end gap-4">
            <!-- Desktop Price -->
            <p class="hidden md:block text-[32px] font-700 text-[#FF8682] text-end">$240<span
                class="text-lg mt-2">/night</span></p>
            <div class="flex flex-row-reverse md:flex-row items-center justify-end gap-3 w-full">
              <div class="flex gap-3">
                <button
                  class="w-12 h-12 border rounded border-[#a2dbc7] hover:bg-gray-50 flex items-center justify-center">
                  <icon name="heroicons-outline:heart" class="text-[#4c4850]"></icon>
                </button>
                <button
                  class="w-12 h-12 border rounded border-[#a2dbc7] hover:bg-gray-50 flex items-center justify-center">
                  <icon name="material-symbols-light:share" class="text-[#4c4850]"></icon>
                </button>
              </div>
              <nuxt-link to="" class="h-12 px-6 text-sm font-600 bg-[#8dd3bb] hover:bg-[#7dc3ab] 
                           text-gray-900 rounded flex items-center justify-center w-full md:w-[150px]">
                Book Now
              </nuxt-link>
            </div>
          </div>
        </div>
      </div>

      <div>
        <div class="grid grid-cols-4 grid-rows-2 gap-2 mt-8">
          <div class="col-span-2 row-span-2">
            <img src="https://justfields.com/storage/projects/7M5rV059/hotel-050.jpg" alt="Hotel main view"
              class="object-cover object-center w-full h-full rounded-md">
          </div>
          <div class="col-start-3">
            <img src="https://justfields.com/storage/projects/7M5rV059/hotel-051.jpg" alt="Hotel room view"
              class="object-cover object-center w-full h-full rounded-md">
          </div>
          <div class="col-start-3 row-start-2">
            <img src="https://justfields.com/storage/projects/7M5rV059/hotel-053.jpg" alt="Hotel amenities"
              class="object-cover object-center w-full h-full rounded-md">
          </div>
          <div class="col-start-4 row-start-1">
            <img src="https://justfields.com/storage/projects/7M5rV059/hotel-052.jpg" alt="Hotel spa"
              class="object-cover object-center w-full h-full rounded-md">
          </div>
          <div class="col-start-4 row-start-2">
            <div class="relative h-full">
              <img src="https://justfields.com/storage/projects/7M5rV059/hotel-054.jpg" alt="Hotel pool"
                class="object-cover object-center w-full h-full rounded-md">
              <div class="absolute bottom-4 end-4 hidden md:block">
                <button class="px-4 py-2 text-sm font-600 bg-[#8DD3BB] rounded hover:bg-[#7bc0a9]">
                  View all photos
                </button>
              </div>
            </div>
          </div>
        </div>
        <!-- Mobile View Button -->
        <div class="md:hidden mt-4 flex items-center justify-center">
          <button class="px-4 py-2 text-sm font-600 bg-[#8DD3BB] rounded hover:bg-[#7bc0a9]">
            View all photos
          </button>
        </div>
      </div>

      <div class="w-full h-0 border my-16 divide-opacity-25"></div>

      <div class="space-y-4">
        <span class="text-xl font-700">Overview</span>
        <p class="text-base font-500">
          Located in Taksim Gmsuyu, the heart of Istanbul, the CVK Park Bosphorus Hotel Istanbul has risen from the
          ashes of the historic Park Hotel, which also served as Foreign Affairs Palace 120 years ago and is hosting its
          guests by assuming this hospitality mission. With its 452 luxurious rooms and suites, 8500 m2 SPA and fitness
          area, 18 meeting rooms including 4 dividable ones and 3 terraces with Bosphorus view, Istanbuls largest
          terrace with Bosphorus view (4500 m2) and latest technology infrastructure, CVK Park Bosphorus Hotel Istanbul
          is destined to be the popular attraction point of the city. Room and suite categories at various sizes with
          city and Bosphorus view, as well as 68 separate luxury suites, are offered to its special guests as a wide
          variety of selection.
        </p>

        <div class="max-w-[870px] mt-8">
          <div class="grid grid-cols-2 gap-2 md:grid-cols-5 md:gap-4">
            <div
              class="border border-gray-300 rounded-md p-3 md:p-4 min-h-[120px] md:min-h-[145px] bg-[#8DD3BB] relative">
              <p class="text-lg md:text-[32px] font-700">4.2</p>
              <div class="absolute bottom-4 satrt-4">
                <div class="mt-2">
                  <p class="text-sm md:text-base font-700 capitalize">very good</p>
                  <p class="mt-1 text-sm font-500">371 reviews</p>
                </div>
              </div>
            </div>
            <div class="border border-gray-300 rounded-md p-3 md:p-4 min-h-[120px] md:min-h-[145px] relative">
              <icon name="bi:stars" class="w-8 h-8" />
              <div class="absolute bottom-4 satrt-4">
                <div class="mt-2">
                  <p class="text-base font-500 capitalize">near park</p>
                </div>
              </div>
            </div>
            <div class="border border-gray-300 rounded-md p-3 md:p-4 min-h-[120px] md:min-h-[145px] relative">
              <icon name="bi:stars" class="w-8 h-8" />
              <div class="absolute bottom-4 satrt-4">
                <div class="mt-2">
                  <p class="text-base font-500 capitalize">near nightlife</p>
                </div>
              </div>
            </div>
            <div class="border border-gray-300 rounded-md p-3 md:p-4 min-h-[120px] md:min-h-[145px] relative">
              <icon name="bi:stars" class="w-8 h-8" />
              <div class="absolute bottom-4 satrt-4">
                <div class="mt-2">
                  <p class="text-base font-500 capitalize">near theater</p>
                </div>
              </div>
            </div>
            <div class="border border-gray-300 rounded-md p-3 md:p-4 min-h-[120px] md:min-h-[145px] relative">
              <icon name="bi:stars" class="w-8 h-8" />
              <div class="absolute bottom-4 satrt-4">
                <div class="mt-2">
                  <p class="text-base font-500 capitalize">clean hotel</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="w-full h-0 border my-16 divide-opacity-25"></div>

      <div>
        <span class="text-xl font-700">Available Rooms</span>
        <div class="mt-8">
          <ul class="space-y-4">
            <li class="flex flex-col md:flex-row items-start md:items-center justify-between py-4 border-b gap-4">
              <div class="flex items-center flex-1">
                <img src="https://justfields.com/storage/projects/7M5rV059/hotel-051.jpg" alt="room-img-01"
                  class="w-12 h-12 rounded me-3.5 flex-shrink-0">
                <span class="font-500 text-base break-words">
                  Superior room - 1 double bed or 2 twin beds
                </span>
              </div>
              <div class="flex flex-col md:flex-row items-start md:items-center gap-4 w-full md:w-auto">
                <p class="font-700 text-2xl whitespace-nowrap">
                  $240<span class="text-sm font-600">/night</span>
                </p>
                <button class="bg-[#8DD3BB] rounded text-sm font-500 w-full md:w-[150px] h-[48px] md:ms-4">
                  Book Now
                </button>
              </div>
            </li>
            <li class="flex flex-col md:flex-row items-start md:items-center justify-between py-4 gap-4">
              <div class="flex flex-1 items-center">
                <img src="https://justfields.com/storage/projects/7M5rV059/hotel-053.jpg" alt="room-img-02"
                  class="w-12 h-12 rounded me-3.5 flex-shrink-0">
                <span class="font-500 text-base break-words">
                  Superior room - City view - 1 double bed or 2 twin beds
                </span>
              </div>
              <div class="flex flex-col md:flex-row items-start md:items-center gap-4 w-full md:w-auto">
                <p class="font-700 text-2xl whitespace-nowrap">
                  $280<span class="text-sm font-600">/night</span>
                </p>
                <button class="bg-[#8DD3BB] rounded text-sm font-500 w-full md:w-[150px] h-[48px] md:ms-4">
                  Book Now
                </button>
              </div>
            </li>
          </ul>
        </div>
      </div>

      <div class="w-full h-0 border my-16 divide-opacity-25"></div>

      <div>
        <div class="flex items-center justify-between">
          <span class="text-xl font-700">Location/Map</span>
          <button class="bg-[#8DD3BB] rounded text-sm font-500 w-[165px] md:w-[189px] h-[48px]">
            View on google maps
          </button>
        </div>
        <div class="inset-0 bg-gray-300 h-[300px] md:h-[450px] mt-8 rounded-3xl">
          <iframe width="100%" height="100%" style="border-radius: 16px"
            src="https://www.openstreetmap.org/export/embed.html?bbox=31.2453%2C29.9294%2C31.3053%2C29.9894&layer=mapnik&marker=29.9594%2C31.2753">
          </iframe>
        </div>
      </div>

      <div class="w-full h-0 border my-16 divide-opacity-25"></div>

      <div>
        <span class="text-xl font-700">Amenities</span>
        <div class="max-w-[1232px] mt-8 md:mt-[34px]">
          <div class="grid grid-cols-2 grid-rows-5 gap-4">
            <div class="flex items-center gap-x-2 group cursor-pointer">
              <icon name="ph:swimming-pool-fill" class="w-5 h-[19px]" />
              <p class="text-base font-500 relative inline-block">
                <span
                  class="relative after:content-[''] after:absolute after:bottom-0 after:start-1/2 after:w-0 after:h-px after:bg-current after:transition-all after:duration-300 group-hover:after:w-full group-hover:after:start-0">
                  Outdoor pool
                </span>
              </p>
            </div>
            <div class="flex items-center gap-x-2 group cursor-pointer">
              <icon name="maki:fitness-centre" class="w-5 h-[19px]" />
              <p class="text-base font-500 relative inline-block">
                <span
                  class="relative after:content-[''] after:absolute after:bottom-0 after:start-1/2 after:w-0 after:h-px after:bg-current after:transition-all after:duration-300 group-hover:after:w-full group-hover:after:start-0">
                  Fitness center
                </span>
              </p>
            </div>
            <div class="flex items-center gap-x-2 group cursor-pointer">
              <icon name="fluent:swimming-pool-32-filled" class="w-5 h-[19px]" />
              <p class="text-base font-500 relative inline-block">
                <span
                  class="relative after:content-[''] after:absolute after:bottom-0 after:start-1/2 after:w-0 after:h-px after:bg-current after:transition-all after:duration-300 group-hover:after:w-full group-hover:after:start-0">
                  Indoor pool
                </span>
              </p>
            </div>
            <div class="flex items-center gap-x-2 group cursor-pointer">
              <icon name="lucide-lab:sunlounger-parasol-sun-palmtree" class="w-5 h-[19px]" />
              <p class="text-base font-500 relative inline-block">
                <span
                  class="relative after:content-[''] after:absolute after:bottom-0 after:start-1/2 after:w-0 after:h-px after:bg-current after:transition-all after:duration-300 group-hover:after:w-full group-hover:after:start-0">
                  Bar/Lounge
                </span>
              </p>
            </div>
            <div class="flex items-center gap-x-2 group cursor-pointer">
              <icon name="material-symbols:spa" class="w-5 h-[19px]" />
              <p class="text-base font-500 relative inline-block">
                <span
                  class="relative after:content-[''] after:absolute after:bottom-0 after:start-1/2 after:w-0 after:h-px after:bg-current after:transition-all after:duration-300 group-hover:after:w-full group-hover:after:start-0">
                  Spa and wellness center
                </span>
              </p>
            </div>
            <div class="flex items-center gap-x-2 group cursor-pointer">
              <icon name="proicons:wi-fi" class="w-5 h-[19px]" />
              <p class="text-base font-500 relative inline-block">
                <span
                  class="relative after:content-[''] after:absolute after:bottom-0 after:start-1/2 after:w-0 after:h-px after:bg-current after:transition-all after:duration-300 group-hover:after:w-full group-hover:after:start-0">
                  Free Wi-Fi
                </span>
              </p>
            </div>
            <div class="flex items-center gap-x-2 group cursor-pointer">
              <icon name="ri:restaurant-fill" class="w-5 h-[19px]" />
              <p class="text-base font-500 relative inline-block">
                <span
                  class="relative after:content-[''] after:absolute after:bottom-0 after:start-1/2 after:w-0 after:h-px after:bg-current after:transition-all after:duration-300 group-hover:after:w-full group-hover:after:start-0">
                  Restaurant
                </span>
              </p>
            </div>
            <div class="flex items-center gap-x-2 group cursor-pointer">
              <icon name="solar:tea-cup-bold" class="w-5 h-[19px]" />
              <p class="text-base font-500 relative inline-block">
                <span
                  class="relative after:content-[''] after:absolute after:bottom-0 after:start-1/2 after:w-0 after:h-px after:bg-current after:transition-all after:duration-300 group-hover:after:w-full group-hover:after:start-0">
                  Tea/coffee machine
                </span>
              </p>
            </div>
            <div class="flex items-center gap-x-2 group cursor-pointer">
              <icon name="material-symbols:room-service" class="w-5 h-[19px]" />
              <p class="text-base font-500 relative inline-block">
                <span
                  class="relative after:content-[''] after:absolute after:bottom-0 after:start-1/2 after:w-0 after:h-px after:bg-current after:transition-all after:duration-300 group-hover:after:w-full group-hover:after:start-0">
                  Room service
                </span>
              </p>
            </div>
            <div class="flex items-center gap-x-2 group cursor-pointer">
              <p class="text-base font-600 text-[#FF8682] relative inline-block">
                <span
                  class="relative after:content-[''] after:absolute after:bottom-0 after:start-1/2 after:w-0 after:h-px after:bg-current after:transition-all after:duration-300 group-hover:after:w-full group-hover:after:start-0">
                  more
                </span>
              </p>
            </div>
          </div>
        </div>
      </div>

      <div class="w-full h-0 border my-16 divide-opacity-25"></div>

      <div>
        <div class="flex items-center justify-between">
          <span class="text-xl font-700">Reviews</span>
          <button class="bg-[#8DD3BB] rounded text-sm font-500 w-[130px] md:w-[152px] h-[48px]">
            Give your review
          </button>
        </div>
        <div class="flex flex-col items-center gap-1 sm:flex-row md:gap-4">
          <div class="overflow-hidden">
            <p class="text-[50px] font-700">4.2</p>
          </div>
          <div>
            <div class="text-center text-sm font-600 sm:text-start md:text-xl">Very Good</div>
            <p class="text-center sm:text-start text-sm font-400">371 verified reviews</p>
          </div>
        </div>
        <div class="w-full h-0 border my-6 divide-opacity-25"></div>
        <div class="mt-8">
          <ul class="space-y-6">
            <li class="flex items-start gap-4 py-2 relative border-b" v-for="user in users" :key="user.name">
              <img :src="user.img" alt="user-avatar" class="w-[45px] h-[45px] rounded-full flex-shrink-0 object-cover">
              <div class="flex-1">
                <div class="flex items-center justify-between">
                  <div class="flex items-center gap-2">
                    <p class="font-600">{{ user.rate }}</p>
                    <span class="text-gray-400">|</span>
                    <p class="font-400">{{ user.name }}</p>
                  </div>
                  <icon name="material-symbols:flag"
                    class="w-5 h-5 text-gray-500 hover:text-[#FF8682] transition-colors" />
                </div>
                <p class="text-sm font-400 mt-2 text-gray-600 max-w-[1135px]">
                  {{ user.desc }}
                </p>
              </div>
            </li>
          </ul>
        </div>

        <div class="flex items-center justify-center mt-6 md:mt-[52px] gap-6">
          <icon name="ic:round-keyboard-arrow-left" class="rtl:rotate-180 cursor-pointer" />
          <p class="text-sm font-400">1 of 40</p>
          <icon name="ic:round-keyboard-arrow-right" class="rtl:rotate-180 cursor-pointer" />
        </div>
      </div>
    </div>
  </div>
</template>