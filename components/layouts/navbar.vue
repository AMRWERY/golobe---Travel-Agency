<script setup lang="ts">
const route = useRoute();
const isOpen = ref(false);
const userMenuOpen = ref(false);

// Check if current route is home page
const isHomePage = computed(() => route.path === '/');

const toggleUserMenu = () => {
    userMenuOpen.value = !userMenuOpen.value;
};
</script>

<template>
    <div>
        <!-- Home Page: Full-screen Hero with built-in navigation -->
        <home-hero v-if="isHomePage" />

        <!-- Other Pages: White Navbar + Separate Hero Section -->
        <template v-else>
            <nav class="h-16 md:h-[90px] bg-white shadow-lg z-50 relative">
                <div class="h-full px-4 sm:px-6 xl:px-[104px]">
                    <!-- Mobile Header -->
                    <div class="flex items-center justify-between h-full md:hidden">
                        <!-- Logo (left on mobile) -->
                        <div class="flex-shrink-0">
                            <nuxt-link to="/">
                                <img class="h-[36px] w-[110.35px]" src="@/assets/golobe-logo-dark.svg" alt="Logo">
                            </nuxt-link>
                        </div>

                        <!-- Hamburger Button -->
                        <button @click="isOpen = !isOpen"
                            class="p-2 text-gray-600 rounded-md hover:text-gray-900 focus:outline-none">
                            <icon name="tabler:menu-deep"></icon>
                        </button>
                    </div>

                    <!-- Desktop Navigation -->
                    <div class="items-center hidden h-full py-4 md:grid md:grid-cols-3">
                        <!-- Left Navigation -->
                        <div class="flex items-center justify-start h-full space-s-8">
                            <nuxt-link to="/flights"
                                class="flex items-center gap-1 text-gray-700 capitalize hover:text-gray-900">
                                <icon name="material-symbols:flight-takeoff-rounded"></icon>
                                <span class="text-sm font-600">find flight</span>
                            </nuxt-link>
                            <nuxt-link to="/hotels"
                                class="flex items-center gap-1 text-gray-700 capitalize hover:text-gray-900">
                                <icon name="material-symbols:king-bed-rounded"></icon>
                                <span class="text-sm font-600">find stays</span>
                            </nuxt-link>
                        </div>

                        <!-- Center Logo -->
                        <div class="flex items-center justify-center h-full md:order-2">
                            <nuxt-link to="/">
                                <img class="w-[110.35px] h-[36px]" src="@/assets/golobe-logo-dark.svg" alt="Logo">
                            </nuxt-link>
                        </div>

                        <!-- Right Navigation -->
                        <div class="flex items-center justify-end h-full space-s-8 md:order-3">
                            <!-- display only if user is not auth -->
                            <nuxt-link to=""
                                class="text-sm text-gray-700 capitalize hover:text-gray-900 font-600">login</nuxt-link>
                            <nuxt-link to="" role="button"
                                class="w-[104px] h-12 bg-[#112211] text-white rounded-lg flex items-center justify-center text-sm font-600 capitalize">sign
                                up</nuxt-link>

                            <!-- display only if user is auth -->
                            <div class="flex items-center justify-center">
                                <nuxt-link to="/favourites" class="flex items-center">
                                    <icon name="heroicons-outline:heart"></icon>
                                    <p class="text-sm font-600 ms-1">Favourites</p>
                                </nuxt-link>
                                <div class="mx-4 h-5 w-0.5 bg-gray-300"></div>

                                <!-- user-dropdown-menu component -->
                                <div class="relative">
                                    <user-dropdown-menu />
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Mobile Menu (Collapsible) -->
                    <transition enter-active-class="transition-all duration-300 ease-out"
                        leave-active-class="transition-all duration-200 ease-in" enter-from-class="opacity-0 max-h-0"
                        enter-to-class="opacity-100 max-h-[800px]" leave-from-class="opacity-100 max-h-[800px]"
                        leave-to-class="opacity-0 max-h-0">
                        <div v-show="isOpen"
                            class="absolute start-0 z-[100] w-full overflow-hidden bg-white md:hidden top-16">
                            <div class="pt-2 pb-3 space-y-1">
                                <nuxt-link to="/flights"
                                    class="flex items-center gap-1 px-3 py-2 text-gray-700 hover:bg-gray-50">
                                    <icon name="material-symbols:flight-takeoff-rounded"></icon>
                                    <span class="text-sm capitalize font-600">find flight</span>
                                </nuxt-link>
                                <nuxt-link to="/hotels"
                                    class="flex items-center gap-1 px-3 py-2 text-gray-700 hover:bg-gray-50">
                                    <icon name="material-symbols:king-bed-rounded"></icon>
                                    <span class="text-sm capitalize font-600">find stays</span>
                                </nuxt-link>
                                <!-- display only if user is not auth -->
                                <nuxt-link to=""
                                    class="flex items-center gap-1 px-3 py-2 text-gray-700 hover:bg-gray-50">
                                    <icon name="material-symbols:login"></icon>
                                    <span class="text-sm capitalize font-600">login</span>
                                </nuxt-link>
                                <nuxt-link to=""
                                    class="flex items-center gap-1 px-3 py-2 text-gray-700 hover:bg-gray-50">
                                    <icon name="mdi:account-plus"></icon>
                                    <span class="text-sm capitalize font-600">sign up</span>
                                </nuxt-link>

                                <!-- display only if user is auth -->
                                <div class="flex items-center px-3 py-2 text-gray-700 hover:bg-gray-50">
                                    <nuxt-link to="/favourites" role="button" class="flex items-center">
                                        <icon name="heroicons-outline:heart"></icon>
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
                </div>
            </nav>
        </template>
    </div>
</template>