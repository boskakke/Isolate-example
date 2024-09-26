<script setup>
import { ref } from 'vue'
import Modal from '@/components/Modal.vue'
import Button from '@/components/Button.vue'

const menuItems = [
  { name: 'Home', link: '/' },
  { name: 'About', link: '/about' },
  { name: 'Contact', link: '/contact' },
  { name: 'Products', link: '/products' },
  { name: 'Services', link: '/services' },
  { name: 'Blog', link: '/blog' },
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

const showModalInline = ref(false)
const showModalTeleport = ref(false)
</script>

<template>
  <Button @click="isolate = !isolate" class="z-40 fixed top-1 left-1">
    Isolate teasers:
    <span :class="isolate ? 'text-green-500' : 'text-red-600'">{{ isolate }}</span>
  </Button>
  <header class="bg-white z-10 fixed top-0 w-full">
    <div class="relative flex gap-4 border-b w-full justify-center">
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

  <main class="grid place-content-center min-h-dvh">
    <div class="flex flex-col gap-4">
      <div class="flex justify-center gap-4">
        <Button @click="showModalInline = true">Open inline modal</Button>
        <Button @click="showModalTeleport = true">Open teleport modal</Button>
      </div>
      <div class="flex gap-2">
        <div
          class="relative w-64 flex flex-col border rounded overflow-hidden"
          :class="{ isolate: isolate }"
          v-for="index in 4"
          :key="index"
        >
          <div class="aspect-square bg-gray-200 relative">
            <img :src="images[index - 1]" alt="product" class="object-cover w-full h-full" />
            <div class="bg-yellow-400 p-1 text-sm absolute top-1 right-1 z-[9999]">Sale Z-9999</div>
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
    </div>

    <Modal v-if="showModalInline" @close-modal="showModalInline = false">
      Inline modal (z-20)
    </Modal>
    <Teleport to="body">
      <Modal v-if="showModalTeleport" @close-modal="showModalTeleport = false">
        Modal that uses Teleport (z-20)
      </Modal>
    </Teleport>
  </main>
</template>
