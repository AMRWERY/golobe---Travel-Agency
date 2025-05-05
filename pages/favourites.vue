<script lang="ts" setup>
const selectedAccommodationType = ref<string>('Flights')

const accommodationTypes = [
  { type: 'Flights', places: 2 },
  { type: 'Hotels', places: 3 },
]

interface BaseCard {
  image: string;
  name: string;
  rating: number;
  reviews: number;
  price: number;
}

interface FlightCard extends BaseCard {
  times: string[];
  stops: string;
  duration: string;
  route: string;
}

interface HotelCard extends BaseCard {
  amenities: string[];
  location: string;
  distance: string;
}

const isHotels = computed(() => selectedAccommodationType.value === 'Hotels');
const isFlights = computed(() => selectedAccommodationType.value === 'Flights');

const flightCards: FlightCard[] = [
  {
    image: 'https://justfields.com/storage/projects/7M5rV059/emirates.png',
    name: 'Emirates',
    rating: 4.2,
    reviews: 54,
    times: ['12.00 pm - 01.28 pm', '12.00 pm - 01.28 pm'],
    stops: 'none stop',
    duration: '2h 28m',
    route: 'EWR-BNA',
    price: 104
  },
  {
    image: 'https://justfields.com/storage/projects/7M5rV059/qatar.png',
    name: 'Qatar Airways',
    rating: 4.2,
    reviews: 54,
    times: ['12.00 pm - 01.28 pm', '12.00 pm - 01.28 pm'],
    stops: 'none stop',
    duration: '2h 28m',
    route: 'EWR-BNA',
    price: 104
  }
];

const hotelCards: HotelCard[] = [
  {
    image: 'https://justfields.com/storage/projects/7M5rV059/hotels-08.jpg',
    name: 'CVK Park Bosphorus Hotel Istanbul',
    rating: 4.8,
    reviews: 371,
    amenities: ['Free Wifi', 'Pool', 'Spa'],
    location: 'Gümüssuyu Mah. Inönü Cad. No:8, Istanbul 34437',
    distance: '1.2 km from center',
    price: 240
  },
  {
    image: 'https://justfields.com/storage/projects/7M5rV059/mariott-Downtown-Dubai.jpg',
    name: 'Eresin Hotels Sultanahmet - Boutique Class',
    rating: 4.5,
    reviews: 54,
    amenities: ['Beach Access', 'Restaurant', 'Gym'],
    location: 'Kucukayasofya No. 40 Sultanahmet, Istanbul 34022',
    distance: '0.5 km from center',
    price: 104
  }
];

const cards = computed(() => {
  if (selectedAccommodationType.value === 'Flights') return flightCards
  if (selectedAccommodationType.value === 'Hotels') return hotelCards
  return []
})
</script>

<template>
  <div>
    <div class="mx-auto md:w-full md:max-w-[1232px] px-4 md:px-0">
      <p class="text-[32px] font-700 mt-12">Favourites</p>
      <div class="bg-white rounded-xl shadow mt-6">
        <div class="flex">
          <button v-for="(accommodation, index) in accommodationTypes" :key="accommodation.type"
            @click="selectedAccommodationType = accommodation.type" class="flex-1 relative px-4 py-6 text-start" :class="[
              index !== accommodationTypes.length - 1 ? 'border-r border-[#D7E2EE]' : '',
              selectedAccommodationType === accommodation.type ? 'border-b-4 border-b-[#8DD3BB]' : ''
            ]">
            <div class="text-base font-600">{{ accommodation.type }}</div>
            <div class="text-sm text-[#112211]/60 font-400">{{ accommodation.places }} places</div>
          </button>
        </div>
      </div>


      <div class="space-y-6 mt-10">
        <div v-for="(card, index) in cards" :key="index"
          class="bg-white rounded-2xl border border-[#8DD3BB]/50 p-4 sm:p-6">
          <div class="flex flex-col sm:flex-row gap-4 sm:gap-8">
            <!-- Left Column (Image) -->
            <div :class="[
              isHotels ? 'w-full sm:w-[300px] h-[200px] sm:h-[298.5px]' : 'w-full sm:w-[180px] h-[110.81px]',
              'shrink-0'
            ]">
              <div class="relative w-full h-full">
                <img :src="card.image" :alt="card.name" class="w-full h-full object-fill rounded-xl">
                <div v-if="isHotels" class="absolute top-3 end-3 bg-white/50 backdrop-blur-sm rounded-lg px-2 py-1">
                  <span class="text-xs">9 images</span>
                </div>
              </div>
            </div>

            <!-- hotels cards -->
            <div class="flex-1 pt-1">
              <template v-if="isHotels">
                <!-- Hotel Name -->
                <div class="flex flex-col sm:flex-row items-start justify-between mb-4 gap-2 sm:gap-0">
                  <div class="w-full sm:w-auto">
                    <h3 class="text-xl leading-6 font-700 text-color break-words">{{ card.name }}</h3>
                  </div>
                  <div class="text-start sm:text-end w-full sm:w-auto">
                    <p class="text-xs font-500 text-color text-start">starting from</p>
                    <div class="flex items-baseline gap-1 text-[#FF8682] sm:justify-end">
                      <span class="text-2xl leading-9 font-700">${{ card.price }}</span>
                      <p class="text-md font-600">/night</p>
                    </div>
                    <p class="text-xs text-color text-end font-500">excl. tax</p>
                  </div>
                </div>
                <!-- Location -->
                <div class="flex items-start sm:items-center gap-2 mb-4">
                  <icon name="material-symbols:location-on" class="w-4 h-4 shrink-0" />
                  <span class="text-xs font-500 break-words">{{ (card as HotelCard).location }}</span>
                </div>
                <!-- Rating & Features -->
                <div class="flex flex-wrap items-center gap-3 sm:gap-6">
                  <div class="flex items-center gap-2">
                    <div class="flex items-center justify-center text-[#FF8682] -space-s-1">
                      <icon name="material-symbols:star-rate" class="w-4 h-4" v-for="n in 5" :key="n" />
                    </div>
                    <span class="text-xs font-500">5 Star Hotel</span>
                  </div>
                  <div class="flex items-center gap-2">
                    <icon name="material-symbols:coffee" class="w-4 h-4" />
                    <p class="text-xs font-500"><span class="font-600">20+</span> Amenities</p>
                  </div>
                </div>
                <div class="flex flex-wrap items-center gap-2 mt-6">
                  <div class="px-2 py-1 rounded border border-[#8DD3BB]">
                    <span class="text-xs font-500 text-color">{{ card.rating }}</span>
                  </div>
                  <div class="ms-1 text-color]">
                    <span class="text-sm font-600">Very Good</span>
                    <span class="text-xs ms-1">{{ card.reviews }} reviews</span>
                  </div>
                </div>
                <div class="flex items-center gap-4 mt-6 pt-6 border-t border-[#8DD3BB]/30">
                  <button class="w-12 h-12 flex items-center justify-center border border-[#8DD3BB] rounded-lg">
                    <icon name="heroicons-outline:heart" class="w-5 h-5" />
                  </button>
                  <nuxt-link to="/hotels-list/1" role="button"
                    class="flex-1 flex items-center justify-center h-12 bg-[#8DD3BB] text-color font-600 rounded-lg hover:bg-[#7bc0a9] text-sm">
                    View Place
                  </nuxt-link>
                </div>
              </template>

              <template v-else>
                <!-- Flight card content -->
                <div class="flex flex-col sm:flex-row items-start justify-between mb-3 gap-2 sm:gap-0">
                  <div class="flex flex-wrap items-center gap-2">
                    <div class="px-2 py-1 rounded border border-[#8DD3BB]">
                      <span class="text-xs font-500 text-color">{{ card.rating }}</span>
                    </div>
                    <div class="ms-1 text-color">
                      <span class="text-sm font-600">Very Good</span>
                      <span class="text-xs ms-1">{{ card.reviews }} reviews</span>
                    </div>
                  </div>
                  <div class="text-start sm:text-right w-full sm:w-auto">
                    <p class="text-xs font-500 text-color text-start">starting from</p>
                    <div class="flex items-baseline gap-1 sm:justify-end">
                      <span class="text-2xl leading-9 font-700 text-[#FF8682]">${{ card.price }}</span>
                    </div>
                  </div>
                </div>
                <!-- Updated Flight Times Section -->
                <div class="flex items-center gap-4 mt-4 max-w-sm">
                  <input type="checkbox" class="w-5 h-5 rounded border-gray-300 text-[#8DD3BB] focus:ring-[#8DD3BB]">
                  <div class="flex-1">
                    <div class="flex items-center gap-4">
                      <div class="flex-1">
                        <div class="text-base font-600">
                          {{ (card as FlightCard).times[0]?.split(' - ')[0] ?? 'N/A' }}
                        </div>
                        <div class="text-sm text-[#112211]/60">{{ card.name }}</div>
                      </div>
                      <div class="flex flex-col items-center px-4">
                        <div class="text-sm text-[#112211]/60">{{ (card as FlightCard).duration }}</div>
                        <div class="flex items-center">
                          <div class="w-2 h-2 rounded-full bg-[#112211]"></div>
                          <div class="w-16 h-[1px] bg-[#112211]"></div>
                          <div class="w-2 h-2 rounded-full bg-[#112211]"></div>
                        </div>
                        <div class="text-sm text-[#112211]/60">{{ (card as FlightCard).stops }}</div>
                      </div>
                      <div class="flex-1 text-right">
                        <div class="text-base font-600">{{ (card as FlightCard).times[0]?.split(' - ')[1] ?? 'N/A' }}
                        </div>
                        <div class="text-sm text-[#112211]/60">{{ (card as FlightCard).route }}</div>
                      </div>
                    </div>
                  </div>
                </div>
                <div class="flex items-center gap-4 mt-6 pt-6 border-t border-[#8DD3BB]/30">
                  <button class="w-12 h-12 flex items-center justify-center border border-[#8DD3BB] rounded-lg">
                    <icon name="heroicons-outline:heart" class="w-5 h-5" />
                  </button>
                  <nuxt-link to="/flights-list/1" role="button"
                    class="flex-1 h-12 flex bg-[#8DD3BB] font-600 rounded-lg hover:bg-[#7bc0a9] items-center justify-center text-center">
                    View Deals
                  </nuxt-link>
                </div>
              </template>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>