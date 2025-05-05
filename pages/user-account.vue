<script lang="ts" setup>
const tabs = ['Account', 'History', 'Payment methods']
const activeTab = ref('Account')
</script>

<template>
  <div>
    <div class="mx-auto md:w-full md:max-w-[1232px] px-4 md:px-0">
      <div class="w-full rounded-2xl overflow-hidden mt-6 md:mt-12">
        <div class="h-[350px] bg-cover bg-center relative" style="background-image: url('/images/profile-cover.jpg')">
          <div class="absolute bottom-4 end-4">
            <!-- desktop screens upload btn -->
            <button
              class="px-4 py-2.5 bg-[#8DD3BB] rounded-md text-sm font-500 hidden md:flex items-center justify-center gap-2">
              <icon name="ic:baseline-cloud-upload" class="w-5 h-5" />
              <span>Upload new cover</span>
            </button>
            <!-- mobile screens upload btn -->
            <button
              class="p-2.5 bg-[#8DD3BB] rounded-full text-sm font-500 flex md:hidden items-center justify-center gap-2">
              <icon name="ic:baseline-cloud-upload" class="w-5 h-5" />
            </button>
          </div>
          <div class="absolute -bottom-12 start-1/2 transform -translate-x-1/2 translate-y-1/4">
            <div class="relative">
              <img class="h-40 w-40 rounded-full border-4 border-[#FF8682] object-cover shadow-lg"
                src="https://images.unsplash.com/photo-1494790108377-be9c29b29330?ixlib=rb-1.2.1&auto=format&fit=crop&w=256&q=80"
                alt="Profile-picture">
              <button
                class="absolute bottom-1 end-1 bg-[#FF8682] hover:bg-[#ff7575] p-2 rounded-full shadow-md transition-colors w-9 h-9">
                <icon name="material-symbols:android-camera" class="w-5 h-5" />
                <span class="sr-only">Upload profile photo</span>
              </button>
            </div>
          </div>
        </div>

        <!-- Profile Info -->
        <div class="pt-16 pb-8 px-6 text-center mt-8">
          <h3 class="text-2xl font-600">Sarah Johnson</h3>
          <p class="font-400 text-base opacity-75">john.doe@gmail.com</p>
        </div>

        <div class=" p-6">
          <!-- Tabs Navigation -->
          <div class="bg-white rounded-xl shadow">
            <div class="flex divide-x-2">
              <button v-for="tab in tabs" :key="tab" @click="activeTab = tab"
                class="flex-1 relative px-4 py-6 text-start hover:bg-gray-50 transition-colors"
                :class="activeTab === tab ? 'border-b-4 border-b-[#8DD3BB]' : ''">
                <div class="text-base font-600">{{ tab }}</div>
              </button>
            </div>
          </div>

          <!-- Tab Content -->
          <div>
            <!-- Account Content -->
            <div v-if="activeTab === 'Account'">
              <!-- account component -->
              <account />
            </div>

            <!-- History Content -->
            <div v-if="activeTab === 'History'">
              <!-- history component -->
              <history />
            </div>

            <!-- Payment Methods Content -->
            <div v-if="activeTab === 'Payment methods'">
              <!-- payment-methods component -->
              <payment-methods />
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>