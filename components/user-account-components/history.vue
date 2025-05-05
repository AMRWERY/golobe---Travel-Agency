<script lang="ts" setup>
const tabs = [
  { title: 'Flights', icon: 'famicons:airplane' },
  { title: 'Stays', icon: 'material-symbols:bed' },
]

const activeTab = ref('Flights')
</script>

<template>
  <div>
    <h3 class="text-[32px] font-700 mb-4 mt-10">Tickets/Bookings</h3>

    <div class="bg-white rounded-xl shadow">
      <div class="flex divide-x-2">
        <button v-for="tab in tabs" :key="tab.title" @click="activeTab = tab.title"
          class="flex-1 relative px-4 py-6 text-start hover:bg-gray-50 transition-colors"
          :class="activeTab === tab.title ? 'border-b-4 border-b-[#8DD3BB]' : ''">
          <div class="flex items-center gap-2">
            <icon :name="tab.icon" class="w-[22px] h-5" />
            <span class="text-base font-600">
              {{ tab.title }}
            </span>
          </div>
        </button>
      </div>
    </div>

    <div>
      <div v-if="activeTab === 'Flights'">
        <div
          class="bg-white rounded-2xl shadow mt-4 p-6 flex flex-col md:flex-row items-center md:justify-between space-y-6 md:space-y-0">
          <div class="flex items-center space-s-6">
            <div class="border border-[#8DD3BB] rounded-xl p-3">
              <img src="https://justfields.com/storage/projects/7M5rV059/emirates.png" alt="Emirates"
                class="h-[44.49px] w-16 object-cover object-center" />
            </div>
            <div class="text-center">
              <p class="text-base font-400 text-gray-500">Newark (EWR)</p>
              <p class="mt-1 text-xl font-600 text-gray-800">12:00 pm</p>
            </div>
            <div class="flex-1 border-t border-dashed border-gray-300 mx-4"></div>
            <div class="text-center">
              <p class="text-base font-400 text-gray-500">Newark (EWR)</p>
              <p class="mt-1 text-xl font-600 text-gray-800">6:00 pm</p>
            </div>
          </div>
          <div class="flex flex-wrap justify-center md:justify-start items-center space-s-6 gap-6">
            <div class="flex flex-col gap-2">
              <div class="flex items-center rounded-md cursor-pointer">
                <div class="bg-[#EBF6F2] p-1 rounded">
                  <icon name="heroicons-solid:calendar-days" class="shrink-0 h-6 w-6 text-[#8DD3BB]" />
                </div>
                <div class="text-start ms-2">
                  <p class="text-xs font-600 text-gray-500">Date</p>
                  <p class="text-base font-500 text-gray-800">12-11-22</p>
                </div>
              </div>
              <div class="flex items-center rounded-md cursor-pointer">
                <div class="bg-[#EBF6F2] p-1 rounded">
                  <icon name="material-symbols:nest-clock-farsight-analog" class="shrink-0 h-6 w-6 text-[#8DD3BB]" />
                </div>
                <div class="text-start ms-2">
                  <p class="text-xs font-600 text-gray-500">Flight time</p>
                  <p class="text-base font-500 text-gray-800">Newark(EWR)</p>
                </div>
              </div>
            </div>
            <div class="flex flex-col gap-2">
              <div class="flex items-center rounded-md cursor-pointer">
                <div class="bg-[#EBF6F2] p-1 rounded">
                  <icon name="material-symbols:door-back" class="shrink-0 h-6 w-6 text-[#8DD3BB]" />
                </div>
                <div class="text-start ms-2">
                  <p class="text-xs font-600 text-gray-500">Gate</p>
                  <p class="text-base font-500 text-gray-800">A12</p>
                </div>
              </div>
              <div class="flex items-center rounded-md cursor-pointer">
                <div class="bg-[#EBF6F2] p-1 rounded">
                  <icon name="material-symbols:airline-seat-recline-extra-rounded"
                    class="shrink-0 h-6 w-6 text-[#8DD3BB]" />
                </div>
                <div class="text-start ms-2">
                  <p class="text-xs font-600 text-gray-500">Seat no.</p>
                  <p class="text-base font-500 text-gray-800">128</p>
                </div>
              </div>
            </div>
          </div>
          <div class="flex items-center space-s-4">
            <button class="px-4 py-2 bg-[#8DD3BB] rounded text-sm font-500">
              Download Ticket
            </button>
            <button class="p-2 hover:bg-green-100 rounded border">
              <icon name="ic:baseline-keyboard-arrow-right" class="h-5 w-5" />
            </button>
          </div>
        </div>
      </div>

      <div v-if="activeTab === 'Stays'">
        <div
          class="bg-white rounded-2xl shadow mt-4 p-6 flex flex-col md:flex-row items-center md:justify-between space-y-6 md:space-y-0">
          <div class="flex items-center space-s-6">
            <div class="border border-[#8DD3BB] rounded-xl p-3">
              <img src="https://justfields.com/storage/projects/7M5rV059/hotel.png" alt="hotel"
                class="h-[44.49px] w-16 object-cover object-center" />
            </div>
            <div class="text-center">
              <p class="text-base font-400 text-gray-500">Newark (EWR)</p>
              <p class="mt-1 text-xl font-600 text-gray-800">12:00 pm</p>
            </div>
            <div class="flex-1 border-t border-dashed border-gray-300 mx-4"></div>
            <div class="text-center">
              <p class="text-base font-400 text-gray-500">Newark (EWR)</p>
              <p class="mt-1 text-xl font-600 text-gray-800">6:00 pm</p>
            </div>
          </div>
          <div class="flex flex-wrap justify-center md:justify-start items-center space-s-6 gap-6">
            <div class="flex flex-col gap-2">
              <div class="flex items-center rounded-md cursor-pointer">
                <div class="bg-[#EBF6F2] p-1 rounded">
                  <icon name="material-symbols:nest-clock-farsight-analog" class="shrink-0 h-6 w-6 text-[#8DD3BB]" />
                </div>
                <div class="text-start ms-2">
                  <p class="text-xs font-600 text-gray-500">Check-In time</p>
                  <p class="text-base font-500 text-gray-800">12:00pm</p>
                </div>
              </div>
              <div class="flex items-center rounded-md cursor-pointer">
                <div class="bg-[#EBF6F2] p-1 rounded">
                  <icon name="material-symbols:nest-clock-farsight-analog" class="shrink-0 h-6 w-6 text-[#8DD3BB]" />
                </div>
                <div class="text-start ms-2">
                  <p class="text-xs font-600 text-gray-500">Check-In out</p>
                  <p class="text-base font-500 text-gray-800">11:30am</p>
                </div>
              </div>
            </div>
            <div class="flex flex-col gap-2">
              <div class="flex items-center rounded-md cursor-pointer">
                <div class="bg-[#EBF6F2] p-1 rounded">
                  <icon name="material-symbols-light:hotel-sharp" class="shrink-0 h-6 w-6 text-[#8DD3BB]" />
                </div>
                <div class="text-start ms-2">
                  <p class="text-xs font-600 text-gray-500">Room no.</p>
                  <p class="text-base font-500 text-gray-800">On arrival</p>
                </div>
              </div>
            </div>
          </div>
          <div class="flex items-center space-s-4">
            <button class="px-4 py-2 bg-[#8DD3BB] rounded text-sm font-500">
              Download Ticket
            </button>
            <button class="p-2 hover:bg-green-100 rounded border">
              <icon name="ic:baseline-keyboard-arrow-right" class="h-5 w-5" />
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>