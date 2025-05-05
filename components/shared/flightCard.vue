<script setup lang="ts">
interface FlightCard {
    image: string;
    name: string;
    rating: number;
    reviews: number;
    times: string[];
    stops: string;
    duration: string;
    route: string;
    price: number;
}

defineProps<{
    card: FlightCard
}>();
</script>

<template>
    <div class="bg-white rounded-2xl border border-[#8DD3BB]/50 p-6">
        <!-- Top Section with Rating and Price -->
        <div class="flex justify-between items-start mb-6">
            <!-- Rating -->
            <div class="flex items-center gap-2">
                <div class="px-2 py-1 bg-[#8DD3BB]/20 rounded">
                    <span class="text-sm font-500">{{ card.rating }}</span>
                </div>
                <span class="text-sm font-500">Very Good</span>
                <span class="text-sm text-[#112211]/60">{{ card.reviews }} reviews</span>
            </div>

            <!-- Price -->
            <div class="text-end">
                <p class="text-sm text-[#112211]/60">starting from</p>
                <p class="text-[32px] font-700 text-[#FF8682]">${{ card.price }}</p>
            </div>
        </div>

        <!-- Logo and Flight Details -->
        <div class="flex gap-8">
            <!-- Airline Logo -->
            <div class="w-[180px] h-[110.81px] shrink-0">
                <img :src="card.image" :alt="card.name" class="w-full h-full object-contain">
            </div>

            <!-- Flight Details -->
            <div class="flex-1">
                <div class="space-y-4">
                    <div v-for="(time, index) in card.times" :key="index" class="flex items-center">
                        <div class="flex items-center gap-3 w-[280px]">
                            <input type="checkbox"
                                class="w-5 h-5 rounded border-gray-300 text-[#8DD3BB] focus:ring-[#8DD3BB]">
                            <div>
                                <div class="text-base">{{ time }}</div>
                                <div class="text-sm text-[#112211]/60">{{ card.name }}</div>
                            </div>
                        </div>
                        <p class="w-[120px] text-sm">{{ card.stops }}</p>
                        <div>
                            <div class="text-base">{{ card.duration }}</div>
                            <div class="text-sm text-[#112211]/60">{{ card.route }}</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Bottom Actions -->
        <div class="flex items-center gap-4 mt-6 pt-6 border-t border-[#8DD3BB]/30">
            <button
                class="w-12 h-12 flex items-center justify-center border border-[#8DD3BB] rounded-lg hover:bg-[#8DD3BB]/10">
                <icon name="heroicons-outline:heart" class="w-5 h-5" />
            </button>
            <button class="flex-1 h-12 bg-[#8DD3BB] font-500 rounded-lg hover:bg-[#7bc0a9]">
                View Deals
            </button>
        </div>
    </div>
</template>

<style scoped>
input[type="checkbox"] {
    accent-color: #8DD3BB;
}
</style>