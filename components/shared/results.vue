<script setup lang="ts">
interface FlightResult {
  airline: string;
  code: string;
  departure: string;
  departureCity: string;
  duration: string;
  arrival: string;
  arrivalCity: string;
  price: number;
}

interface HotelResult {
  hotel: string;
  location: string;
  rating: number;
  amenities: string[];
  price: number;
}

interface ResultsData<T> {
  title: string;
  filters: string[];
  results: T[];
}

const props = defineProps<{
  type: 'flights' | 'hotels'
}>();

const flightData: ResultsData<FlightResult> = {
  title: 'Flight Results',
  filters: ['Price', 'Duration', 'Airlines'],
  results: [
    {
      airline: 'Pakistan Airlines',
      code: 'PK-123',
      departure: '09:30 AM',
      departureCity: 'Lahore',
      duration: '2h 30m',
      arrival: '12:00 PM',
      arrivalCity: 'Karachi',
      price: 250
    },
    {
      airline: 'Pakistan Airlines',
      code: 'PK-124',
      departure: '10:30 AM',
      departureCity: 'Lahore',
      duration: '2h 30m',
      arrival: '01:00 PM',
      arrivalCity: 'Karachi',
      price: 300
    },
    {
      airline: 'Pakistan Airlines',
      code: 'PK-125',
      departure: '11:30 AM',
      departureCity: 'Lahore',
      duration: '2h 30m',
      arrival: '02:00 PM',
      arrivalCity: 'Karachi',
      price: 350
    }
  ]
};

const hotelData: ResultsData<HotelResult> = {
  title: 'Hotel Results',
  filters: ['Price', 'Rating', 'Amenities'],
  results: [
    {
      hotel: 'Luxury Resort & Spa',
      location: 'Maldives',
      rating: 4.8,
      amenities: ['Pool', 'Spa', 'Restaurant'],
      price: 299
    },
    {
      hotel: 'Mountain View Lodge',
      location: 'Swiss Alps',
      rating: 4.6,
      amenities: ['Skiing', 'Restaurant', 'Spa'],
      price: 199
    },
    {
      hotel: 'City Center Hotel',
      location: 'New York',
      rating: 4.5,
      amenities: ['Gym', 'Restaurant', 'Business Center'],
      price: 159
    }
  ]
};

const data = computed(() => props.type === 'flights' ? flightData : hotelData);
</script>

<template>
    <div>
        <!-- Flight results content -->
        <div class="py-8">
            <div class="flex items-center justify-between">
                <h2 class="mb-6 title-style">{{ data.title }}</h2>
                <nuxt-link :to="`/${props.type}-list`" role="button" class="outline-btn-block">
                    See all
                </nuxt-link>
            </div>

            <!-- Flight filters -->
            <div class="mb-6 rounded-lg bg-gray-50">
                <div class="flex flex-wrap items-center gap-4">
                    <div class="font-500">Filters:</div>
                    <button v-for="filter in data.filters" :key="filter" 
                            class="px-3 py-1 text-sm bg-white border border-gray-300 rounded">
                        {{ filter }}
                    </button>
                </div>
            </div>

            <!-- Flight results -->
            <div class="space-y-4">
                <template v-if="props.type === 'flights'">
                    <div v-for="(result, i) in (data as typeof flightData).results" :key="i" 
                         class="p-6 bg-white border border-gray-100 rounded-lg shadow-sm">
                        <div class="flex flex-col gap-4 md:flex-row md:items-center md:justify-between">
                            <div class="flex items-center gap-4">
                                <div class="flex items-center justify-center w-12 h-12 bg-gray-100 rounded-full">
                                    <span class="font-600">{{ result.airline[0] }}</span>
                                </div>
                                <div>
                                    <div class="font-600">{{ result.airline }}</div>
                                    <div class="text-sm text-gray-500">Flight {{ result.code }}</div>
                                </div>
                            </div>
                            <div class="flex items-center gap-8">
                                <div class="text-center">
                                    <div class="font-600">{{ result.departure }}</div>
                                    <div class="text-sm text-gray-500">{{ result.departureCity }}</div>
                                </div>
                                <div class="flex flex-col items-center">
                                    <div class="text-xs text-gray-500">{{ result.duration }}</div>
                                    <div class="relative w-24 h-px my-1 bg-gray-300">
                                        <div class="absolute right-0 w-2 h-2 transform rotate-45 bg-gray-300 -top-1"></div>
                                    </div>
                                    <div class="text-xs text-gray-500">Direct</div>
                                </div>
                                <div class="text-center">
                                    <div class="font-600">{{ result.arrival }}</div>
                                    <div class="text-sm text-gray-500">{{ result.arrivalCity }}</div>
                                </div>
                            </div>
                            <div class="text-right">
                                <div class="text-xl font-600">${{ result.price }}</div>
                                <button class="mt-2 px-4 py-2 bg-[#8DD3BB] rounded-md text-sm font-500">
                                    Book Now
                                </button>
                            </div>
                        </div>
                    </div>
                </template>
                <template v-else>
                    <div v-for="(result, i) in (data as typeof hotelData).results" :key="i" 
                         class="p-6 bg-white border border-gray-100 rounded-lg shadow-sm">
                        <div class="flex flex-col gap-4 md:flex-row md:items-center md:justify-between">
                            <div class="flex items-center gap-4">
                                <div class="flex items-center justify-center w-12 h-12 bg-gray-100 rounded-full">
                                    <span class="font-600">{{ result.hotel[0] }}</span>
                                </div>
                                <div>
                                    <div class="font-600">{{ result.hotel }}</div>
                                    <div class="text-sm text-gray-500">{{ result.location }}</div>
                                </div>
                            </div>
                            <div class="flex items-center gap-4">
                                <div class="flex items-center">
                                    <span class="text-yellow-400">★</span>
                                    <span class="ml-1">{{ result.rating }}</span>
                                </div>
                                <div class="flex flex-wrap gap-2">
                                    <span v-for="amenity in result.amenities" :key="amenity" 
                                          class="px-2 py-1 bg-gray-100 rounded-full text-sm">
                                        {{ amenity }}
                                    </span>
                                </div>
                            </div>
                            <div class="text-right">
                                <div class="text-xl font-600">${{ result.price }}</div>
                                <button class="mt-2 px-4 py-2 bg-[#8DD3BB] rounded-md text-sm font-500">
                                    Book Now
                                </button>
                            </div>
                        </div>
                    </div>
                </template>
            </div>

            <!-- Mobile "See more" button -->
            <div class="flex justify-center mt-6 md:hidden">
                <button role="button" class="outline-btn">
                    See All
                </button>
            </div>
        </div>
    </div>
</template>