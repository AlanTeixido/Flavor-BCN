<template>
  <section id="about" class="py-24 px-6 relative overflow-hidden">
    <!-- Subtle gold accent -->
    <div class="absolute top-0 left-1/2 -translate-x-1/2 w-px h-24 bg-gradient-to-b from-transparent to-gold/30"></div>

    <div ref="aboutContainer" class="max-w-6xl mx-auto">
      <div class="grid md:grid-cols-2 gap-16 items-center">
        <!-- Image side -->
        <div ref="aboutImage" class="relative">
          <div class="aspect-[4/5] bg-gradient-to-br from-gold/20 via-gold/5 to-transparent rounded-sm overflow-hidden">
            <div
              class="w-full h-full bg-cover bg-center"
              style="background-image: url('https://images.unsplash.com/photo-1577219491135-ce391730fb2c?w=800&q=80')"
            ></div>
          </div>
          <!-- Decorative border offset -->
          <div class="absolute -bottom-4 -right-4 w-full h-full border border-gold/20 rounded-sm -z-10"></div>
        </div>

        <!-- Text side -->
        <div ref="aboutText">
          <div class="flex items-center gap-3 mb-6">
            <div class="w-10 h-px bg-gold"></div>
            <span class="text-gold text-xs tracking-[0.3em] uppercase font-semibold">Sobre Nosaltres</span>
          </div>

          <h2 class="font-serif text-4xl md:text-5xl font-bold text-white mb-8 leading-tight">
            Una passió pel
            <span class="text-gradient-gold italic"> sabor</span>
          </h2>

          <p class="text-white/60 leading-relaxed mb-6">
            Flavor BCN neix de la visió del xef <strong class="text-white/90">Marc Puigdomènech</strong>,
            un cuiner format als millors restaurants de Barcelona i la costa mediterrània.
            Amb més de 15 anys d'experiència, el Marc combina la tradició culinària catalana
            amb tècniques d'avantguarda.
          </p>

          <p class="text-white/60 leading-relaxed mb-8">
            La nostra filosofia és simple: producte de proximitat, respecte pel temporada
            i una execució impecable. Cada plat explica una història del Mediterrani,
            des dels mercats de la Boqueria fins a les aigües de la Costa Brava.
          </p>

          <div class="flex items-center gap-6">
            <div class="text-center">
              <p class="font-serif text-3xl font-bold text-gold">15+</p>
              <p class="text-xs text-white/40 tracking-wider mt-1">ANYS</p>
            </div>
            <div class="w-px h-12 bg-white/10"></div>
            <div class="text-center">
              <p class="font-serif text-3xl font-bold text-gold">Km0</p>
              <p class="text-xs text-white/40 tracking-wider mt-1">PRODUCTE LOCAL</p>
            </div>
            <div class="w-px h-12 bg-white/10"></div>
            <div class="text-center">
              <p class="font-serif text-3xl font-bold text-gold">1</p>
              <p class="text-xs text-white/40 tracking-wider mt-1">ESTRELLA MICHELIN</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'

gsap.registerPlugin(ScrollTrigger)

const aboutImage = ref(null)
const aboutText = ref(null)

onMounted(() => {
  gsap.from(aboutImage.value, {
    x: -60,
    opacity: 0,
    duration: 1,
    ease: 'power3.out',
    scrollTrigger: {
      trigger: aboutImage.value,
      start: 'top 80%',
    },
  })

  gsap.from(aboutText.value.children, {
    y: 40,
    opacity: 0,
    stagger: 0.15,
    duration: 0.8,
    ease: 'power3.out',
    scrollTrigger: {
      trigger: aboutText.value,
      start: 'top 80%',
    },
  })
})
</script>
