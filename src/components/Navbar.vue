<template>
  <nav
    ref="navbar"
    class="fixed top-0 left-0 right-0 z-50 transition-all duration-500"
    :class="scrolled ? 'bg-dark/95 backdrop-blur-md shadow-lg shadow-black/20' : 'bg-transparent'"
  >
    <div class="max-w-7xl mx-auto px-6 py-4 flex items-center justify-between">
      <!-- Logo -->
      <a href="#hero" class="flex items-center gap-2 group">
        <span class="font-serif text-2xl font-bold text-gold tracking-wide group-hover:text-gold-light transition-colors">
          Flavor
        </span>
        <span class="font-serif text-2xl font-light text-white/80">BCN</span>
      </a>

      <!-- Desktop Links -->
      <div class="hidden md:flex items-center gap-8">
        <a
          v-for="link in links"
          :key="link.href"
          :href="link.href"
          class="text-sm text-white/60 hover:text-gold transition-colors duration-300 tracking-wide"
        >
          {{ link.label }}
        </a>
        <a
          href="#reserva"
          class="px-6 py-2.5 bg-gold text-dark text-sm font-semibold tracking-wider hover:bg-gold-light transition-all duration-300 rounded-sm"
        >
          Reserva
        </a>
      </div>

      <!-- Mobile Toggle -->
      <button
        class="md:hidden text-white/80 hover:text-gold transition-colors"
        @click="mobileOpen = !mobileOpen"
      >
        <Icon :icon="mobileOpen ? 'mdi:close' : 'mdi:menu'" class="w-7 h-7" />
      </button>
    </div>

    <!-- Mobile Menu -->
    <transition
      enter-active-class="transition-all duration-300 ease-out"
      leave-active-class="transition-all duration-200 ease-in"
      enter-from-class="opacity-0 -translate-y-2"
      leave-to-class="opacity-0 -translate-y-2"
    >
      <div v-if="mobileOpen" class="md:hidden bg-dark/98 backdrop-blur-md border-t border-white/5 px-6 py-6">
        <a
          v-for="link in links"
          :key="link.href"
          :href="link.href"
          class="block py-3 text-white/70 hover:text-gold transition-colors border-b border-white/5 last:border-0"
          @click="mobileOpen = false"
        >
          {{ link.label }}
        </a>
        <a
          href="#reserva"
          class="block mt-4 text-center px-6 py-3 bg-gold text-dark font-semibold tracking-wider hover:bg-gold-light transition-all rounded-sm"
          @click="mobileOpen = false"
        >
          Reserva
        </a>
      </div>
    </transition>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { Icon } from '@iconify/vue'

const scrolled = ref(false)
const mobileOpen = ref(false)

const links = [
  { label: 'Sobre Nosaltres', href: '#about' },
  { label: 'La Carta', href: '#carta' },
  { label: 'Experiència', href: '#experiencia' },
  { label: 'Galeria', href: '#galeria' },
]

function onScroll() {
  scrolled.value = window.scrollY > 50
}

onMounted(() => window.addEventListener('scroll', onScroll))
onUnmounted(() => window.removeEventListener('scroll', onScroll))
</script>
