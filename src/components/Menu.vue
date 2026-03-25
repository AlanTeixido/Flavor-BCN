<template>
  <section id="carta" class="py-24 px-6 relative">
    <!-- Section header -->
    <div ref="menuHeader" class="text-center mb-16 max-w-2xl mx-auto">
      <div class="flex items-center justify-center gap-3 mb-6">
        <div class="w-10 h-px bg-gold"></div>
        <Icon icon="mdi:silverware-fork-knife" class="text-gold w-5 h-5" />
        <div class="w-10 h-px bg-gold"></div>
      </div>
      <h2 class="font-serif text-4xl md:text-5xl font-bold text-white mb-4">La Carta</h2>
      <p class="text-white/50 italic font-serif">Cuina de mercat, producte de temporada</p>
    </div>

    <!-- Category tabs -->
    <div class="flex justify-center gap-2 mb-12 flex-wrap">
      <button
        v-for="(cat, idx) in menuCategories"
        :key="cat.name"
        @click="activeCategory = idx"
        class="px-6 py-2.5 text-sm tracking-wider transition-all duration-300 rounded-sm"
        :class="activeCategory === idx
          ? 'bg-gold text-dark font-semibold'
          : 'border border-white/10 text-white/50 hover:border-gold/30 hover:text-gold'"
      >
        {{ cat.name }}
      </button>
    </div>

    <!-- Dishes grid -->
    <div class="max-w-5xl mx-auto">
      <transition-group
        name="dish"
        tag="div"
        class="grid sm:grid-cols-2 gap-4"
      >
        <div
          v-for="(item, idx) in menuCategories[activeCategory].items"
          :key="item.name"
          ref="dishCards"
          class="group relative bg-white/[0.03] border border-white/5 rounded-sm p-6 cursor-pointer overflow-hidden transition-all duration-500 hover:border-gold/20"
          :style="{ transitionDelay: `${idx * 80}ms` }"
        >
          <!-- Gold overlay on hover -->
          <div class="absolute inset-0 bg-gradient-to-br from-gold/5 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500"></div>

          <div class="relative flex items-start justify-between gap-4">
            <div class="flex-1">
              <div class="flex items-center gap-3 mb-2">
                <span class="text-2xl">{{ item.emoji }}</span>
                <h3 class="font-serif text-lg font-semibold text-white group-hover:text-gold transition-colors duration-300">
                  {{ item.name }}
                </h3>
              </div>
              <p class="text-white/40 text-sm leading-relaxed">{{ item.description }}</p>
            </div>
            <div class="font-serif text-xl font-bold text-gold shrink-0">
              {{ item.price }}€
            </div>
          </div>

          <!-- Bottom gold line on hover -->
          <div class="absolute bottom-0 left-0 right-0 h-px bg-gold/40 scale-x-0 group-hover:scale-x-100 transition-transform duration-500 origin-left"></div>
        </div>
      </transition-group>
    </div>
  </section>
</template>

<script setup>
import { ref, watch, onMounted, nextTick } from 'vue'
import { Icon } from '@iconify/vue'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import { menuCategories } from '../data/menu.js'

gsap.registerPlugin(ScrollTrigger)

const activeCategory = ref(0)
const menuHeader = ref(null)
const dishCards = ref([])

onMounted(() => {
  gsap.from(menuHeader.value.children, {
    y: 30,
    opacity: 0,
    stagger: 0.1,
    duration: 0.8,
    ease: 'power3.out',
    scrollTrigger: {
      trigger: menuHeader.value,
      start: 'top 80%',
    },
  })
})

// Animate dishes when category changes — slide in from kitchen
watch(activeCategory, async () => {
  await nextTick()
  const cards = document.querySelectorAll('#carta .group')
  gsap.from(cards, {
    x: 60,
    opacity: 0,
    stagger: 0.08,
    duration: 0.6,
    ease: 'power3.out',
  })
})
</script>

<style scoped>
.dish-enter-active {
  transition: all 0.5s ease-out;
}
.dish-leave-active {
  transition: all 0.3s ease-in;
}
.dish-enter-from {
  opacity: 0;
  transform: translateX(40px);
}
.dish-leave-to {
  opacity: 0;
  transform: translateX(-20px);
}
</style>
