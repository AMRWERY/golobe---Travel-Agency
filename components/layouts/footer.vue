<script setup lang="ts">
const emailAddress = ref('');

const handleSubscribe = () => {
  console.log('Subscribing with email:', emailAddress.value);
  // Reset the input field
  emailAddress.value = '';
};
</script>

<template>
  <div class="min-h-screen flex flex-col">
    <div class="flex-grow">
      <!-- This div will push the footer down -->
    </div>
    <footer class="mt-12 md:mt-[90px] w-full">
      <!-- Newsletter subscription section -->
      <div class="px-4 mx-auto sm:px-6 max-w-[1232px] mb-[-100px] relative z-20">
        <div class="p-6 bg-[#cdeae1] rounded-[20px] relative shadow-md">
          <div class="grid items-stretch h-full grid-cols-1 gap-6 lg:grid-cols-5">
            <!-- Left content -->
            <div class="flex flex-col justify-between lg:col-span-3 max-w-[593px]">
              <div>
                <h2 class="text-3xl font-700 text-[#213322] md:text-[44px] mb-6 w-[364px] leading-10">Subscribe
                  Newsletter</h2>
                <h3 class="text-xl font-700 text-[#4a5e50] mb-2">The Travel</h3>
                <p class="mb-4 text-[#576e5f] text-base font-500">Get inspired! Receive travel discounts, tips and
                  behind the scenes
                  stories.</p>
              </div>

              <div class="flex flex-col space-y-4 sm:flex-row sm:space-y-0 sm:space-s-4">
                <input type="email" v-model="emailAddress" placeholder="Your email address"
                  class="flex-1 px-4 py-3 border border-gray-200 rounded" />
                <button @click="handleSubscribe"
                  class="px-6 py-3 text-white bg-[#112211] rounded hover:bg-[#223322] transition-colors">
                  Subscribe
                </button>
              </div>
            </div>

            <!-- Right image -->
            <div class="relative hidden h-full lg:col-span-2 lg:block">
              <div class="absolute bottom-0 end-6 -top-9" style="transform: translateX(20%)">
                <icon name="twemoji:open-mailbox-with-lowered-flag" class="w-[250px] h-[350px]"></icon>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- Navigation section -->
      <div class="bg-[#8DD3BB] py-12 pt-[120px] relative z-10">
        <div class=" px-4 mx-auto sm:px-6 max-w-[1232px]">
          <div class="grid grid-cols-1 gap-8 mt-6 md:grid-cols-5 lg:mt-16">
            <div class="md:col-span-1">
              <!-- Logo and social icons -->
              <div class="h-[83.15px] w-[120px]">
                <nuxt-link to="/" class="inline-block w-[120px] h-[39px]">
                  <img class="h-auto" src="@/assets/golobe-logo-footer.svg" alt="Golobe Logo">
                </nuxt-link>
                <div class="flex mt-6 space-x-[12px]">
                  <nuxt-link to="" class="text-[#112211]">
                    <icon name="mdi:facebook"></icon>
                  </nuxt-link>
                  <nuxt-link to="" class="text-[#112211]">
                    <icon name="mdi:twitter"></icon>
                  </nuxt-link>
                  <nuxt-link to="" class="text-[#112211]">
                    <icon name="mdi:youtube"></icon>
                  </nuxt-link>
                  <nuxt-link to="" class="text-[#112211]">
                    <icon name="tabler:brand-instagram-filled"></icon>
                  </nuxt-link>
                </div>
              </div>
            </div>

            <div class="md:col-span-4">
              <div class="grid grid-cols-2 gap-6 md:grid-cols-5 lg:gap-8">
                <div>
                  <h3 class="mb-4 text-base font-700 text-[#1f3725]">Our Destinations</h3>
                  <ul class="space-y-3">
                    <li>
                      <nuxt-link to=""
                        class="text-sm font-500 text-[#49735e] hover:text-[#223322]">Canada</nuxt-link>
                    </li>
                    <li>
                      <nuxt-link to=""
                        class="text-sm font-500 text-[#49735e] hover:text-[#223322]">Alaska</nuxt-link>
                    </li>
                    <li>
                      <nuxt-link to=""
                        class="text-sm font-500 text-[#49735e] hover:text-[#223322]">France</nuxt-link>
                    </li>
                    <li>
                      <nuxt-link to=""
                        class="text-sm font-500 text-[#49735e] hover:text-[#223322]">Iceland</nuxt-link>
                    </li>
                  </ul>
                </div>

                <div>
                  <h3 class="mb-4 text-base font-700 text-[#1f3725]">Our Activities</h3>
                  <ul class="space-y-3">
                    <li>
                      <nuxt-link to="" class="text-sm font-500 text-[#49735e] hover:text-[#223322]">Northern
                        Lights</nuxt-link>
                    </li>
                    <li>
                      <nuxt-link to="" class="text-sm font-500 text-[#49735e] hover:text-[#223322]">Cruising &
                        sailing</nuxt-link>
                    </li>
                    <li>
                      <nuxt-link to=""
                        class="text-sm font-500 text-[#49735e] hover:text-[#223322]">Multi-activities</nuxt-link>
                    </li>
                    <li>
                      <nuxt-link to=""
                        class="text-sm font-500 text-[#49735e] hover:text-[#223322]">Kayaking</nuxt-link>
                    </li>
                  </ul>
                </div>

                <div>
                  <h3 class="mb-4 text-base font-700 text-[#1f3725]">Travel Blogs</h3>
                  <ul class="space-y-3">
                    <li>
                      <nuxt-link to="" class="text-sm font-500 text-[#49735e] hover:text-[#223322]">Bali Travel
                        Guide</nuxt-link>
                    </li>
                    <li>
                      <nuxt-link to="" class="text-sm font-500 text-[#49735e] hover:text-[#223322]">Sri Lanka Travel
                        Guide</nuxt-link>
                    </li>
                    <li>
                      <nuxt-link to="" class="text-sm font-500 text-[#49735e] hover:text-[#223322]">Peru Travel
                        Guide</nuxt-link>
                    </li>
                    <li>
                      <nuxt-link to="" class="text-sm font-500 text-[#49735e] hover:text-[#223322]">Bali Travel
                        Guide</nuxt-link>
                    </li>
                  </ul>
                </div>

                <div>
                  <h3 class="mb-4 text-base font-700 text-[#1f3725]">About Us</h3>
                  <ul class="space-y-3">
                    <li>
                      <nuxt-link to="" class="text-sm font-500 text-[#49735e] hover:text-[#223322]">Our
                        Story</nuxt-link>
                    </li>
                    <li>
                      <nuxt-link to="" class="text-sm font-500 text-[#49735e] hover:text-[#223322]">Work with
                        us</nuxt-link>
                    </li>
                  </ul>
                </div>

                <div>
                  <h3 class="mb-4 text-base font-700 text-[#1f3725]">Contact Us</h3>
                  <ul class="space-y-3">
                    <li>
                      <nuxt-link to="" class="text-sm font-500 text-[#49735e] hover:text-[#223322]">Our
                        Story</nuxt-link>
                    </li>
                    <li>
                      <nuxt-link to="" class="text-sm font-500 text-[#49735e] hover:text-[#223322]">Work with
                        us</nuxt-link>
                    </li>
                  </ul>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>