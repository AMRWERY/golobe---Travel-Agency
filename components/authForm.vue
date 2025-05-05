<script setup lang="ts">
defineProps<{
    show: boolean
}>()

const isRegistering = ref(false)
const showPassword = ref(false)

const formData = ref({
    username: '',
    email: '',
    password: ''
})

const togglePasswordVisibility = () => {
    showPassword.value = !showPassword.value
}

const submitForm = (event: Event) => {
    event.preventDefault()
    if (isRegistering.value) {
        // Register logic
        if (!formData.value.username || !formData.value.email || !formData.value.password) {
            alert('Please fill all registration fields')
            return
        }
        console.log('Registering with:', formData.value)
    } else {
        // Login logic
        if (!formData.value.email || !formData.value.password) {
            alert('Please fill all login fields')
            return
        }
        console.log('Logging in with:', formData.value)
    }
    // Clear form after submission
    formData.value = { username: '', email: '', password: '' }
}
</script>

<template>
    <div>
        <transition enter-active-class="transition-all duration-300 ease-out" enter-from-class="opacity-0 max-h-0"
            enter-to-class="opacity-100 max-h-[500px]">
            <div v-if="show" class="mt-4 overflow-hidden">
                <div class="space-y-4">
                    <form @submit="submitForm" class="space-y-4">
                        <div class="relative" v-if="isRegistering">
                            <input v-model="formData.username" type="text" placeholder="Username"
                                class="w-full px-4 py-3 border border-gray-200 rounded pe-10">
                            <icon name="mdi:account-outline"
                                class="absolute end-3 top-1/2 -translate-y-1/2 text-gray-400" />
                        </div>

                        <div class="relative">
                            <input v-model="formData.email" type="email" placeholder="Email address"
                                class="w-full px-4 py-3 border border-gray-200 rounded pe-10">
                            <icon name="mdi:email-outline"
                                class="absolute end-3 top-1/2 -translate-y-1/2 text-gray-400" />
                        </div>

                        <div class="relative">
                            <input v-model="formData.password" :type="showPassword ? 'text' : 'password'"
                                placeholder="Password" class="w-full px-4 py-3 border border-gray-200 rounded pe-10">
                            <button type="button" @click="togglePasswordVisibility"
                                class="absolute end-3 top-1/2 -translate-y-1/2 text-gray-400">
                                <icon :name="showPassword ? 'mdi:eye-off' : 'mdi:eye'" />
                            </button>
                        </div>

                        <button type="submit"
                            class="w-full flex justify-center items-center h-12 px-2 text-sm font-600 tracking-wide text-color bg-[#8dd3bb] rounded">
                            {{ isRegistering ? 'Register' : 'Login' }}
                        </button>
                    </form>

                    <div class="flex items-center justify-center p-4 bg-gray-100">
                        <p class="text-sm text-center text-gray-500">
                            {{ isRegistering ? 'Already have an account?' : "Don't have an account?" }}
                            <button @click="isRegistering = !isRegistering"
                                class="text-indigo-500 transition duration-100 hover:text-indigo-600 active:text-indigo-700">
                                {{ isRegistering ? 'Login' : 'Register' }}
                            </button>
                        </p>
                    </div>
                </div>
            </div>
        </transition>
    </div>
</template>