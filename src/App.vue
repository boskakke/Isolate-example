<script setup>
import { ref } from 'vue'

const menuItems = [
  { name: 'Home', link: '/' },
  { name: 'About', link: '/about' },
  { name: 'Contact', link: '/contact' },
  { name: 'Products', link: '/products' },
  { name: 'Services', link: '/services' },
  { name: 'Blog', link: '/blog' },
  { name: 'Careers', link: '/careers' },
  { name: 'FAQ', link: '/faq' },
  { name: 'Support', link: '/support' },
  { name: 'Privacy', link: '/privacy' },
  { name: 'Terms', link: '/terms' },
  { name: 'Sitemap', link: '/sitemap' },
  { name: 'Login', link: '/login' },
  { name: 'Register', link: '/register' },
  { name: 'Logout', link: '/logout' }
]

const images = [
  'https://assets-imgix.hobbii.com/image/catalog/2023/4/1681718032_front-latest.jpg?fm=jpg&w=300&h=300&q=50&dpr=2',
  'https://assets-imgix.hobbii.com/image/catalog/2021/4/rb-bamboo-front.jpg?fm=jpg&w=300&h=300&q=50&dpr=2',
  'https://assets-imgix.hobbii.com/image/catalog/2021/11/easy-care-classic-front.jpg?fm=jpg&w=300&h=300&q=50&dpr=2',
  'https://assets-imgix.hobbii.com/image/catalog/2024/3/everyday-acrylic-xl-front.jpg?fm=jpg&w=300&h=300&q=50&dpr=2'
]
const isolate = ref(false)
</script>

<template>
  <header class="bg-white z-10 fixed top-0 w-full">
    <div class="relative flex gap-4 border-b w-full justify-center">
      <button @click="isolate = !isolate">
        Isolate: <span :class="isolate ? 'text-green-500' : 'text-red-600'">{{ isolate }}</span>
      </button>
      <div v-for="item in menuItems" :key="item.name" class="p-4 relative group">
        <span>
          {{ item.name }}
        </span>
        <div class="group-hover:flex hidden flex-col absolute top-full w-40 shadow-md">
          <a
            v-for="(item, index) in 15"
            :key="index"
            class="p-4 bg-white border-b border-gray-200 w-full"
          >
            Menu-item-{{ index }}
          </a>
        </div>
      </div>
    </div>
  </header>

  <main class="grid place-content-center h-[200dvh]">
    <div class="flex gap-2">
      <div
        class="relative w-64 flex flex-col border rounded overflow-hidden"
        :class="{ isolate: isolate }"
        v-for="index in 4"
        :key="index"
      >
        <div class="aspect-square bg-gray-200 relative">
          <img :src="images[index - 1]" alt="product" class="object-cover w-full h-full" />
          <div class="bg-yellow-400 p-1 text-sm absolute top-1 right-1 z-50">Sale</div>
        </div>
        <div class="p-2">
          <div class="font-bold text-sm">Title</div>
          <div class="mt-2 text-sm">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Neque nulla, eum dolorem
            recusandae nesciunt hic deleniti commodi eos.
          </div>
        </div>
      </div>
    </div>
  </main>
</template>
