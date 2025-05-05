<script setup lang="ts">
const reviews = [
    {
        quote: "A real sense of community, nurtured",
        text: "Really appreciate the help and support from the staff during these tough times. Shoutout to Katie for...",
        name: "Olga",
        location: "Weave Studios - Kai Tak",
        image: "https://images.unsplash.com/photo-1475070929565-c985b496cb9f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80"
    },
    {
        quote: "The facilities are superb. Clean, slick, bright.",
        text: "\"A real sense of community, nurtured\"Really appreciate the help and support from the staff...",
        name: "Thomas",
        location: "Weave Studios - Olympic",
        image: "https://images.unsplash.com/photo-1475070929565-c985b496cb9f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80"
    },
    {
        quote: "A real sense of community, nurtured",
        text: "Really appreciate the help and support from the staff during these tough times. Shoutout to Katie for...",
        name: "Eliot",
        location: "Weave Studios - Kai Tak",
        image: "https://images.unsplash.com/photo-1475070929565-c985b496cb9f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80"
    },
    {
        quote: "Great atmosphere, friendly staff",
        text: "The place has a wonderful environment and the staff is always ready to help. Would recommend to anyone looking...",
        name: "Sarah",
        location: "Weave Studios - Central",
        image: "https://images.unsplash.com/photo-1475070929565-c985b496cb9f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80"
    }
];

// Create an extended array for infinite scrolling
const displayedReviews = computed(() => {
    // Add duplicates of the first 2 items at the end for infinite loop effect
    return [...reviews, ...reviews.slice(0, 2)];
});

// Carousel state
const carouselPosition = ref(0);
const carouselInterval = ref<number | null>(null);
const carouselTrack = ref<HTMLElement | null>(null);
const isResetting = ref(false);

// Mouse drag state
let isDragging = false;
let startPosition = 0;
let currentTranslate = 0;

// Setup automatic scrolling
onMounted(() => {
    startAutoScroll();
    setupDragListeners();
});

// Clean up on unmount
onUnmounted(() => {
    stopAutoScroll();
    removeDragListeners();
});

// Methods to control scrolling
const startAutoScroll = () => {
    carouselInterval.value = window.setInterval(() => {
        if (!isDragging) {
            nextSlide();
        }
    }, 3000);
};

const stopAutoScroll = () => {
    if (carouselInterval.value) {
        clearInterval(carouselInterval.value);
        carouselInterval.value = null;
    }
};

const nextSlide = () => {
    carouselPosition.value += 1;
    // If we're at the duplicate section, prepare to seamlessly reset
    if (carouselPosition.value >= reviews.length) {
        updateCarousel();
        // Wait for transition to complete, then quick jump to the real first slide without animation
        setTimeout(() => {
            isResetting.value = true;
            carouselPosition.value = carouselPosition.value % reviews.length;
            updateCarousel(true);
            // Re-enable transition after the reset
            setTimeout(() => {
                isResetting.value = false;
            }, 50);
        }, 500);
    } else {
        updateCarousel();
    }
};

const prevSlide = () => {
    if (carouselPosition.value === 0) {
        // Quick jump to the last duplicate without animation
        isResetting.value = true;
        carouselPosition.value = reviews.length - 1;
        updateCarousel(true);
        // Re-enable transition after the jump
        setTimeout(() => {
            isResetting.value = false;
        }, 50);
    } else {
        carouselPosition.value -= 1;
        updateCarousel();
    }
};

const moveToSlide = (index: number) => {
    carouselPosition.value = index;
    updateCarousel();
};

const updateCarousel = (skipTransition = false) => {
    if (!carouselTrack.value) return;
    // Remove transition when doing a reset
    if (skipTransition || isResetting.value) {
        carouselTrack.value.style.transition = 'none';
    } else {
        carouselTrack.value.style.transition = 'transform 0.5s ease-out';
    }
    const translateX = carouselPosition.value * -33.33;
    carouselTrack.value.style.transform = `translateX(${translateX}%)`;
    currentTranslate = translateX;
};

// Drag functionality
const setupDragListeners = () => {
    const track = carouselTrack.value;
    if (!track) return;
    // Mouse events
    track.addEventListener('mousedown', dragStart);
    track.addEventListener('mousemove', drag);
    track.addEventListener('mouseup', dragEnd);
    track.addEventListener('mouseleave', dragEnd);
    // Touch events
    track.addEventListener('touchstart', dragStart);
    track.addEventListener('touchmove', drag);
    track.addEventListener('touchend', dragEnd);
};

const removeDragListeners = () => {
    const track = carouselTrack.value;
    if (!track) return;
    // Mouse events
    track.removeEventListener('mousedown', dragStart);
    track.removeEventListener('mousemove', drag);
    track.removeEventListener('mouseup', dragEnd);
    track.removeEventListener('mouseleave', dragEnd);
    // Touch events
    track.removeEventListener('touchstart', dragStart);
    track.removeEventListener('touchmove', drag);
    track.removeEventListener('touchend', dragEnd);
};

const dragStart = (e: MouseEvent | TouchEvent) => {
    stopAutoScroll();
    isDragging = true;
    // Get starting position
    if (e instanceof MouseEvent) {
        startPosition = e.clientX;
    } else {
        startPosition = e.touches[0].clientX;
    }
    // Remove transition during drag
    if (carouselTrack.value) {
        carouselTrack.value.style.transition = 'none';
    }
};

const drag = (e: MouseEvent | TouchEvent) => {
    if (!isDragging || !carouselTrack.value) return;
    // Get current position
    let currentPosition = 0;
    if (e instanceof MouseEvent) {
        currentPosition = e.clientX;
    } else {
        currentPosition = e.touches[0].clientX;
    }
    // Calculate move distance
    const diff = currentPosition - startPosition;
    const movePercent = (diff / carouselTrack.value.clientWidth) * 100;
    // Update transform
    const newTranslate = currentTranslate + movePercent;
    carouselTrack.value.style.transform = `translateX(${newTranslate}%)`;
};

const dragEnd = () => {
    if (!isDragging || !carouselTrack.value) return;
    isDragging = false;
    // Add transition back
    carouselTrack.value.style.transition = 'transform 0.5s ease-out';
    // Snap to nearest slide or stay at current if movement was small
    const snapThreshold = 15; // 15% movement threshold for slide change
    if (carouselTrack.value.style.transform) {
        const currentTransform = parseFloat(carouselTrack.value.style.transform.replace('translateX(', '').replace('%)', ''));
        const originalSlidePosition = carouselPosition.value * -33.33;
        const diff = currentTransform - originalSlidePosition;
        if (diff > snapThreshold && carouselPosition.value > 0) {
            // Moved right enough to go to previous slide
            prevSlide();
        } else if (diff < -snapThreshold && carouselPosition.value < displayedReviews.value.length - 1) {
            // Moved left enough to go to next slide
            nextSlide();
        } else {
            // Not enough movement, stay at current slide
            updateCarousel();
        }
    }
    // Restart auto scroll
    startAutoScroll();
};

// Event handlers for pausing auto scroll
const handleMouseEnter = () => {
    stopAutoScroll();
};

const handleMouseLeave = () => {
    if (!isDragging) {
        startAutoScroll();
    }
};
</script>

<template>
    <div>
        <div class="mx-auto">
            <!-- Header section -->
            <div class="flex items-center justify-between mb-10 mt-[70px]">
                <div>
                    <h2 class="title-style">Reviews</h2>
                    <p class="subtitle-style">What people says about Golobe facilities
                    </p>
                </div>
                <button
                    class="outline-btn-block">
                    See All
                </button>
            </div>

            <!-- Review carousel container -->
            <div class="relative overflow-hidden" @mouseenter="handleMouseEnter" @mouseleave="handleMouseLeave">
                <!-- Carousel track -->
                <div ref="carouselTrack"
                    class="flex gap-[26px] transition-transform duration-500 cursor-grab active:cursor-grabbing"
                    style="transform: translateX(0%)">
                    <!-- Review cards -->
                    <div v-for="(review, index) in displayedReviews" :key="`review-${index}`"
                        class="min-w-[300px] md:min-w-[425px] h-full">
                        <div class="relative h-full pb-3 -pt-2 pe-3">
                            <!-- Colored background element -->
                            <div
                                class="absolute bottom-0 end-0 w-[calc(100%-8px)] h-[calc(100%-8px)] bg-[#ceebe2] rounded-[20px] -z-10">
                            </div>
                            <!-- Card content -->
                            <div
                                class="relative p-6 transition-shadow bg-white border rounded-[20px] shadow-sm border-gray-50 hover:shadow-md flex flex-col h-[600px]">
                                <!-- Quote -->
                                <h3 class="text-2xl font-700 mb-4">{{ review.quote }}</h3>

                                <!-- Review text -->
                                <p class="mb-4 text-sm text-gray-600 font-500">{{ review.text }}</p>

                                <!-- View more link -->
                                <div class="flex justify-end mb-4">
                                    <nuxt-link to="" class="text-base font-700 text-[#293829] hover:underline">View
                                        more</nuxt-link>
                                </div>

                                <!-- Star rating -->
                                <div class="flex mb-5">
                                    <span v-for="star in 5" :key="star" class="text-[#ffc107]">
                                        <icon name="material-symbols:star" class="w-[22.5px] h-[21px]"></icon>
                                    </span>
                                </div>

                                <!-- Reviewer info -->
                                <div class="flex items-center justify-between mb-4">
                                    <div>
                                        <p class="font-700 text-[#1f2f1f] text-sm mb-1">{{ review.name }}</p>
                                        <p class="text-xs text-[#b5bab5] font-500">{{ review.location }}</p>
                                        <div class="flex items-center mt-3">
                                            <icon name="logos:google-icon"></icon>
                                            <span class="text-xs text-[#c0c5c0] ms-1 font-700">Google</span>
                                        </div>
                                    </div>
                                </div>

                                <!-- Image -->
                                <div class="w-full h-48 mt-auto overflow-hidden rounded-lg">
                                    <img :src="review.image" :alt="review.name" class="object-cover w-full h-full">
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Navigation dots -->
                <div class="flex justify-center mt-6 space-x-2">
                    <button v-for="(_, index) in reviews" :key="index" @click="moveToSlide(index)"
                        class="w-2 h-2 transition-all rounded-full"
                        :class="carouselPosition % reviews.length === index ? 'bg-[#8DD3BB] w-4' : 'bg-gray-300'"></button>
                </div>
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