<script setup lang="ts">
const props = defineProps<{
    isMobile?: boolean;
    isLight?: boolean;
}>();

const isOpen = ref(false);

const toggleDropdown = () => {
    isOpen.value = !isOpen.value;
};

// Close dropdown when clicking outside
const closeOnClickOutside = (event: MouseEvent) => {
    const dropdown = document.getElementById('dropdownMenu');
    const button = document.getElementById('dropdownToggle');

    if (dropdown && button &&
        !button.contains(event.target as Node) &&
        !dropdown.contains(event.target as Node)) {
        isOpen.value = false;
    }
};

// Add event listener when component mounts
onMounted(() => {
    document.addEventListener('click', closeOnClickOutside);
});

// Cleanup event listener
onBeforeUnmount(() => {
    document.removeEventListener('click', closeOnClickOutside);
});
</script>

<template>
    <div>
        <div :class="[
            'relative',
            isMobile ? 'w-full' : 'w-max'
        ]">
            <button type="button" id="dropdownToggle" class="flex items-center" @click.stop="toggleDropdown">
                <div class="relative">
                    <img class="h-11 w-11 rounded-full object-cover"
                        src="https://randomuser.me/api/portraits/women/87.jpg" alt="user-avatar">
                    <div class="absolute inset-0 rounded-full shadow-inner"></div>
                </div>
                <div class="ms-1">
                    <h2 :class="[
                        'font-600 text-sm',
                        isLight ? 'text-white' : 'text-color'
                    ]">Jane Doe</h2>
                    <p v-if="isMobile" class="text-sm font-400 text-color">Online</p>
                </div>
            </button>

            <!-- Desktop Dropdown -->
            <ul v-if="!isMobile" id="dropdownMenu" :class="[
                'absolute end-0 shadow-[0_8px_19px_-7px_rgba(6,81,237,0.2)] bg-white p-4 z-[1000]',
                'w-[329px] max-h-auto divide-y overflow-auto',
                { 'hidden': !isOpen }
            ]">
                <div class="flex items-center border-gray-200 mb-5">
                    <div class="relative">
                        <img class="h-16 w-16 rounded-full object-cover"
                            src="https://randomuser.me/api/portraits/women/87.jpg" alt="user-avatar">
                        <div class="absolute inset-0 rounded-full shadow-inner"></div>
                    </div>
                    <div class="ms-4">
                        <h2 class="font-600 text-color text-base">Jane Doe</h2>
                        <p class="text-color text-sm font-400">Online</p>
                    </div>
                </div>
                <div class="space-y-6">
                    <div class="group border-b py-3 space-y-4">
                        <li
                            class="dropdown-item px-5 hover:bg-gray-50 text-slate-900 text-sm font-500 cursor-pointer flex items-center justify-between gap-2 py-1.5">
                            <nuxt-link to="/user-account" class="flex items-center gap-2">
                                <icon name="mdi:account" class="w-[15px] h-5"></icon>
                                <span>My Account</span>
                            </nuxt-link>
                            <icon name="ic:round-keyboard-arrow-right" class="w-5 h-5" />
                        </li>
                        <li
                            class="dropdown-item px-5 hover:bg-gray-50 text-slate-900 text-sm font-500 cursor-pointer flex items-center justify-between gap-2 py-1.5">
                            <div class="flex items-center gap-2">
                                <icon name="ic:baseline-settings" class="w-[15px] h-5"></icon>
                                <span>Settings</span>
                            </div>
                            <icon name="ic:round-keyboard-arrow-right" class="w-5 h-5" />
                        </li>
                    </div>
                    <div class="group space-y-4">
                        <li
                            class='dropdown-item px-5 hover:bg-gray-50 text-slate-900 text-sm font-500 cursor-pointer flex items-center gap-2 py-1.5'>
                            <icon name="mynaui:logout" class="w-[15px] h-5"></icon>
                            <span>Logout</span>
                        </li>
                    </div>
                </div>
            </ul>

            <!-- Mobile Dropdown Content -->
            <div v-else class="w-full" :class="{ 'hidden': !isOpen }">
                <div class="space-y-1">
                    <nuxt-link to="/user-account" class="flex items-center gap-2 px-3 py-2 text-gray-700 hover:bg-gray-50">
                        <icon name="mdi:account" class="w-[15px] h-5"></icon>
                        <span class="text-sm font-500">My Account</span>
                    </nuxt-link>
                    <nuxt-link to="" class="flex items-center gap-2 px-3 py-2 text-gray-700 hover:bg-gray-50">
                        <icon name="ic:baseline-settings" class="w-[15px] h-5"></icon>
                        <span class="text-sm font-500">Settings</span>
                    </nuxt-link>
                    <nuxt-link to="" class="flex items-center gap-2 px-3 py-2 text-gray-700 hover:bg-gray-50">
                        <icon name="mynaui:logout" class="w-[15px] h-5"></icon>
                        <span class="text-sm font-500">Logout</span>
                    </nuxt-link>
                </div>
            </div>
        </div>
    </div>
</template>