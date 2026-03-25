<template>
  <section id="galeria" class="py-24 px-6">
    <div ref="galHeader" class="text-center mb-16">
      <div class="flex items-center justify-center gap-3 mb-6">
        <div class="w-10 h-px bg-gold"></div>
        <Icon icon="mdi:camera" class="text-gold w-5 h-5" />
        <div class="w-10 h-px bg-gold"></div>
      </div>
      <h2 class="font-serif text-4xl md:text-5xl font-bold text-white mb-4">Galeria</h2>
      <p class="text-white/50 italic font-serif">Moments que es queden</p>
    </div>

    <div ref="galGrid" class="gallery-grid max-w-6xl mx-auto">
      <div
        v-for="(item, idx) in gallery"
        :key="idx"
        class="group relative overflow-hidden rounded-sm cursor-pointer"
        :class="item.tall ? 'aspect-[3/4]' : 'aspect-[4/3]'"
      >
        <!-- Gradient placeholder -->
        <div
          class="w-full h-full transition-transform duration-700 group-hover:scale-110"
          :style="{ background: item.gradient }"
        ></div>

        <!-- Gold overlay on hover -->
        <div class="absolute inset-0 bg-gold/0 group-hover:bg-gold/20 transition-all duration-500"></div>

        <!-- Label -->
        <div class="absolute bottom-0 left-0 right-0 p-4 bg-gradient-to-t from-dark/80 to-transparent translate-y-full group-hover:translate-y-0 transition-transform duration-500">
          <p class="font-serif text-sm text-white">{{ item.label }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import { Icon } from '@iconify/vue'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

const galHeader = ref(null)
const galGrid = ref(null)

const gallery = [
  { gradient: 'linear-gradient(135deg, #C9A84C33 0%, #0a0a0a 50%, #C9A84C22 100%)', label: 'Interior del restaurant', tall: true },
  { gradient: 'linear-gradient(225deg, #C9A84C22 0%, #1a1a1a 40%, #C9A84C11 100%)', label: 'Tartar de tonyina', tall: false },
  { gradient: 'linear-gradient(180deg, #C9A84C15 0%, #0f0f0f 60%, #C9A84C33 100%)', label: 'La nostra cuina', tall: false },
  { gradient: 'linear-gradient(45deg, #0a0a0a 0%, #C9A84C22 50%, #0a0a0a 100%)', label: 'Detalls de la sala', tall: false },
  { gradient: 'linear-gradient(315deg, #C9A84C28 0%, #111111 45%, #C9A84C18 100%)', label: 'Xef Marc en acció', tall: true },
  { gradient: 'linear-gradient(160deg, #1a1a1a 0%, #C9A84C20 50%, #0a0a0a 100%)', label: 'Postres artesanals', tall: false },
]

onMounted(() => {
  gsap.from(galHeader.value.children, {
    y: 30,
    opacity: 0,
    stagger: 0.1,
    duration: 0.8,
    ease: 'power3.out',
    scrollTrigger: { trigger: galHeader.value, start: 'top 80%' },
  })

  gsap.from(galGrid.value.children, {
    y: 40,
    opacity: 0,
    scale: 0.95,
    stagger: 0.1,
    duration: 0.6,
    ease: 'power3.out',
    scrollTrigger: { trigger: galGrid.value, start: 'top 85%' },
  })
})
</script>
