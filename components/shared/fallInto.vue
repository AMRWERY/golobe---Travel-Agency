<script setup lang="ts">
import { computed } from 'vue';

const props = defineProps<{
  type: 'flights' | 'hotels'
}>();

const flightPlaces = [
  {
    title: 'Melbourne',
    subtitle: 'An amazing journey',
    price: '700',
    img: 'https://justfields.com/storage/projects/7M5rV059/Melbourne.jpg'
  },
  {
    title: 'Paris',
    subtitle: 'A Paris Adventure',
    price: '600',
    img: 'https://justfields.com/storage/projects/7M5rV059/Paris.jpg'
  },
  {
    title: 'London',
    subtitle: 'London eye adventure',
    price: '350',
    img: 'https://justfields.com/storage/projects/7M5rV059/London.jpg'
  },
  {
    title: 'Columbia',
    subtitle: 'Amazing streets',
    price: '700',
    img: 'https://justfields.com/storage/projects/7M5rV059/Columbia.jpg'
  }
];

const hotelPlaces = [
  {
    title: 'Maldives Resort',
    subtitle: 'Luxury beachfront experience',
    price: '899',
    img: 'https://justfields.com/storage/projects/7M5rV059/Maldives-Resort.jpg'
  },
  {
    title: 'Swiss Chalet',
    subtitle: 'Mountain view retreat',
    price: '599',
    img: 'https://justfields.com/storage/projects/7M5rV059/Swiss-Chalet.jpg'
  },
  {
    title: 'NYC Hotel',
    subtitle: 'City center luxury',
    price: '399',
    img: 'https://justfields.com/storage/projects/7M5rV059/NYC-Hotel.jpg'
  },
  {
    title: 'Dubai Palace',
    subtitle: 'Desert oasis resort',
    price: '799',
    img: 'https://justfields.com/storage/projects/7M5rV059/Dubai-Palace.jpg'
  }
];

const places = computed(() => props.type === 'flights' ? flightPlaces : hotelPlaces);
const title = computed(() => props.type === 'flights' ? 'Fall into travel' : 'Find your perfect stay');
const subtitle = computed(() => props.type === 'flights'
  ? "Going somewhere to celebrate this season? Whether you're going home or somewhere to roam, we've got the travel tools to get you to your destination."
  : "Looking for the perfect place to stay? From luxury resorts to cozy mountain lodges, we've got you covered.");
const buttonText = computed(() => props.type === 'flights' ? 'Book Flight' : 'Book Hotel');
const seeAllLink = computed(() => props.type === 'flights' ? '/flights-list' : '/hotels-list');

const featureContent = computed(() => ({
  flights: {
    title: 'Fall into travel',
    subtitle: "Going somewhere to celebrate this season? Whether you're going home or somewhere to roam, we've got the travel tools to get you to your destination.",
    mainCard: {
      title1: 'Backpacking',
      title2: 'Sri Lanka',
      price: '700',
      description: "Traveling is a unique experience as it's the best way to unplug from the pushes and pulls of daily life. It helps us to forget about our problems, frustrations, and fears at home. During our journey, we experience life in different ways. We explore new places, cultures, cuisines, traditions, and ways of living.",
      buttonText: 'Book flight'
    },
    images: [
      'https://justfields.com/storage/projects/7M5rV059/card-img-1.jpg',
      'https://justfields.com/storage/projects/7M5rV059/card-img-2.jpg',
      'https://justfields.com/storage/projects/7M5rV059/card-img-3.jpg',
      'https://justfields.com/storage/projects/7M5rV059/card-img-4.jpg'
    ]
  },
  hotels: {
    title: 'Discover Amazing Places',
    subtitle: "From luxurious resorts to cozy boutique hotels, find the perfect accommodation for your dream vacation.",
    mainCard: {
      title1: 'Luxury',
      title2: 'Maldives',
      price: '899',
      description: "Experience ultimate luxury in the heart of paradise. Our handpicked Maldives resorts offer pristine beaches, crystal-clear waters, and world-class amenities. Whether you're seeking a romantic getaway or a family adventure, these exclusive properties promise an unforgettable stay.",
      buttonText: 'Book hotel'
    },
    images: [
      'https://justfields.com/storage/projects/7M5rV059/hotels-05.jpg',
      'https://justfields.com/storage/projects/7M5rV059/hotels-06.jpg',
      'https://justfields.com/storage/projects/7M5rV059/hotels-07.jpg',
      'https://justfields.com/storage/projects/7M5rV059/hotels-08.jpg'
    ]
  }
}));

const currentFeature = computed(() => featureContent.value[props.type]);
</script>

<template>
  <div>
    <div class="py-12">
      <!-- Header section -->
      <div class="flex items-center justify-between mb-8">
        <div>
          <h2 class="title-style">{{ title }}</h2>
          <p class="subtitle-style max-w-[851px]">{{ subtitle }}</p>
        </div>
        <nuxt-link :to="seeAllLink" role="button" class="outline-btn-block">
          See all
        </nuxt-link>
      </div>

      <div class="grid grid-cols-1 gap-4 sm:grid-cols-2 md:grid-cols-4">
        <div
          class="relative overflow-hidden transition-shadow shadow-lg w-full lg:w-[296px] h-[420px] rounded-2xl hover:shadow-xl"
          v-for="place in places" :key="place.title">
          <img :src="place.img" alt="card-img" class="absolute object-cover object-center w-full h-full">
          <div class="absolute bottom-0 p-6 text-white end-0 start-0 bg-gradient-to-t from-black/60 to-transparent">
            <div class="flex items-end justify-between mb-4">
              <div>
                <p class="text-2xl font-600">{{ place.title }}</p>
                <p class="mb-1 text-sm font-400">{{ place.subtitle }}</p>
              </div>
              <div class="text-end">
                <p class="mb-2 text-2xl font-600">${{ place.price }}</p>
              </div>
            </div>
            <button
              class="w-full px-5 py-3 font-500 text-black transition-colors bg-[#8dd3bb] rounded hover:bg-green-500 text-sm hover:text-white">
              {{ buttonText }}
            </button>
          </div>
        </div>
      </div>

      <div class="flex justify-center mt-6 md:hidden">
        <nuxt-link :to="seeAllLink" role="button" class="outline-btn">
          See all
        </nuxt-link>
      </div>
    </div>

    <div class="pt-10 pb-12">
      <!-- Header section -->
      <div class="flex items-center justify-between mb-8">
        <div>
          <h2 class="title-style">{{ currentFeature.title }}</h2>
          <p class="subtitle-style max-w-[1000px]">{{ currentFeature.subtitle }}</p>
        </div>
        <nuxt-link :to="seeAllLink" role="button" class="outline-btn-block">
          See all
        </nuxt-link>
      </div>

      <div class="p-4 mx-auto">
        <div class="grid grid-cols-1 gap-6 md:grid-cols-2">
          <!-- First Main Column - Content Card -->
          <div
            class="overflow-hidden transition-shadow bg-[#8dd3bb] shadow-lg rounded-[20px] hover:shadow-xl max-w-[552px] h-[424px]">
            <div class="flex flex-col h-full p-6">
              <div class="flex flex-row items-start justify-between">
                <div class="flex flex-col mb-4 md:mb-0">
                  <h2 class="text-[40px] font-700">{{ currentFeature.mainCard.title1 }}</h2>
                  <h2 class="text-[40px] font-700">{{ currentFeature.mainCard.title2 }}</h2>
                </div>
                <div class="p-2 bg-white rounded-lg md:ms-6 w-[68px] h-[62px] flex items-center flex-col mt-4">
                  <p class="text-sm font-400 capitalize">from</p>
                  <p class="text-xl font-600">${{ currentFeature.mainCard.price }}</p>
                </div>
              </div>
              <p class="mb-4 text-sm text-[#48705c] font-400">{{ currentFeature.mainCard.description }}</p>
              <div class="mt-auto">
                <button
                  class="w-full py-3 text-sm text-black transition-colors bg-white hover:bg-green-500 hover:text-white">
                  {{ currentFeature.mainCard.buttonText }}
                </button>
              </div>
            </div>
          </div>

          <!-- Second Main Column - Grid of Image Cards -->
          <div class="grid grid-cols-2 gap-4">
            <!-- Sub Column 1 -->
            <div class="space-y-6">
              <div class="overflow-hidden aspect-video rounded-2xl hover:shadow-xl max-w-[318px] h-[200px]">
                <img :src="currentFeature.images[0]" alt="feature-img-1" class="object-cover w-full h-full">
              </div>
              <div class="overflow-hidden aspect-video rounded-2xl hover:shadow-xl max-w-[318px] h-[200px]">
                <img :src="currentFeature.images[2]" alt="feature-img-3" class="object-cover w-full h-full">
              </div>
            </div>

            <!-- Sub Column 2 -->
            <div class="space-y-6">
              <div class="overflow-hidden aspect-video rounded-2xl hover:shadow-xl max-w-[318px] h-[200px]">
                <img :src="currentFeature.images[1]" alt="feature-img-2" class="object-cover w-full h-full">
              </div>
              <div class="overflow-hidden aspect-video rounded-2xl hover:shadow-xl max-w-[318px] h-[200px]">
                <img :src="currentFeature.images[3]" alt="feature-img-4" class="object-cover w-full h-full">
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="flex justify-center mt-6 md:hidden">
        <nuxt-link :to="seeAllLink" role="button" class="outline-btn">
          See all
        </nuxt-link>
      </div>
    </div>
  </div>
</template>