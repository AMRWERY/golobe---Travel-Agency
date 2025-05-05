<script setup lang="ts">
interface Card {
    image: string
}

const cards = ref<Card[]>([
    { image: 'https://justfields.com/storage/projects/7M5rV059/img-02.jpg' },
    { image: 'https://justfields.com/storage/projects/7M5rV059/img-03.jpg' },
    { image: 'https://justfields.com/storage/projects/7M5rV059/img-04.jpg' },
    { image: 'https://justfields.com/storage/projects/7M5rV059/img-05.jpg' },
    { image: 'https://justfields.com/storage/projects/7M5rV059/img-06.jpg' },
    { image: 'https://justfields.com/storage/projects/7M5rV059/img-07.jpg' },
    { image: 'https://justfields.com/storage/projects/7M5rV059/img-04.jpg' },
])

const displayedCards = [...cards.value, ...cards.value.slice(0, 2)];
</script>

<template>
    <div>
        <div class="mt-6 relative overflow-hidden group">
            <div class="flex justify-center">
                <div
                    class="grid grid-cols-3 sm:grid-cols-3 md:grid-cols-5 lg:grid-cols-9 gap-3 md:gap-4 justify-items-center">
                    <div v-for="(card, index) in displayedCards" :key="index"
                        class="w-[120px] h-[120px] aspect-square rounded-xl overflow-hidden shadow-lg hover:scale-105 transition-transform">
                        <img :src="card.image" class="w-full h-full object-cover" :alt="`Card ${index + 1}`">
                    </div>
                </div>
            </div>
        </div>

        <div class="w-full min-h-[102px] bg-[#8DD3BB] mt-10 rounded-lg p-3 md:p-4">
            <p class="capitalize text-xl md:text-2xl font-700 text-color">
                Emirates airlines policies
            </p>
            <div class="mt-4 md:mt-[18px] flex flex-col md:flex-row gap-4 md:gap-6">
                <div class="flex items-center md:max-w-[571px] w-full">
                    <icon name="material-symbols:timer-rounded" class="w-[18px] h-[19.5px] flex-shrink-0 me-4"></icon>
                    <p class="text-sm md:text-base text-color font-500 leading-tight">
                        Pre-flight cleaning, installation of cabin HEPA filters.
                    </p>
                </div>
                <div class="flex items-center md:max-w-[571px] w-full">
                    <icon name="material-symbols:timer-rounded" class="w-[18px] h-[19.5px] flex-shrink-0 me-4"></icon>
                    <p class="text-sm md:text-base text-color font-500 leading-tight">
                        Pre-flight health screening questions.
                    </p>
                </div>
            </div>
        </div>
    </div>
</template>