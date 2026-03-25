<template>
  <section id="hero" ref="heroSection" class="relative h-screen flex items-center justify-center overflow-hidden">
    <!-- Background with parallax -->
    <div
      ref="heroBg"
      class="absolute inset-0 bg-cover bg-center scale-110"
      style="background-image: url('https://images.unsplash.com/photo-1414235077428-338989a2e8c0?w=1920&q=80')"
    ></div>

    <!-- Dark overlay -->
    <div class="absolute inset-0 bg-dark/70"></div>

    <!-- Gold vignette -->
    <div class="absolute inset-0 bg-gradient-to-t from-dark via-transparent to-dark/40"></div>

    <!-- Content -->
    <div ref="heroContent" class="relative z-10 text-center px-6 max-w-4xl">
      <!-- Decorative line -->
      <div class="flex items-center justify-center gap-4 mb-8">
        <div class="w-16 h-px bg-gold/40"></div>
        <Icon icon="mdi:silverware-variant" class="text-gold w-5 h-5" />
        <div class="w-16 h-px bg-gold/40"></div>
      </div>

      <h1 class="font-serif text-5xl sm:text-6xl md:text-8xl font-bold text-white mb-6 leading-tight">
        Flavor <span class="text-gradient-gold">BCN</span>
      </h1>

      <p class="font-serif text-lg sm:text-xl md:text-2xl text-white/70 italic mb-10 max-w-2xl mx-auto">
        Cuina mediterrània d'autor a Barcelona
      </p>

      <div class="flex flex-col sm:flex-row items-center justify-center gap-4">
        <a
          href="#carta"
          class="px-10 py-4 bg-gold text-dark font-semibold tracking-widest text-sm hover:bg-gold-light transition-all duration-300 rounded-sm"
        >
          DESCOBREIX LA CARTA
        </a>
        <a
          href="#reserva"
          class="px-10 py-4 border border-gold/40 text-gold text-sm tracking-widest hover:bg-gold/10 transition-all duration-300 rounded-sm"
        >
          RESERVA TAULA
        </a>
      </div>

      <!-- Scroll indicator -->
      <div class="absolute bottom-10 left-1/2 -translate-x-1/2 animate-bounce">
        <Icon icon="mdi:chevron-double-down" class="text-gold/50 w-6 h-6" />
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

const heroSection = ref(null)
const heroBg = ref(null)
const heroContent = ref(null)

onMounted(() => {
  // Parallax on background
  gsap.to(heroBg.value, {
    yPercent: 30,
    ease: 'none',
    scrollTrigger: {
      trigger: heroSection.value,
      start: 'top top',
      end: 'bottom top',
      scrub: true,
    },
  })

  // Fade out content on scroll
  gsap.to(heroContent.value, {
    opacity: 0,
    y: -60,
    ease: 'none',
    scrollTrigger: {
      trigger: heroSection.value,
      start: '30% top',
      end: 'bottom top',
      scrub: true,
    },
  })

  // Entrance animation
  const tl = gsap.timeline({ defaults: { ease: 'power3.out' } })
  tl.from(heroContent.value.children, {
    y: 40,
    opacity: 0,
    stagger: 0.15,
    duration: 1,
    delay: 0.3,
  })
})
</script>
