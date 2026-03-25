<template>
  <section id="experiencia" class="py-24 px-6 relative overflow-hidden">
    <!-- Background accent -->
    <div class="absolute inset-0 bg-gradient-to-b from-transparent via-gold/[0.02] to-transparent"></div>

    <div class="max-w-6xl mx-auto relative">
      <div ref="expHeader" class="text-center mb-16">
        <div class="flex items-center justify-center gap-3 mb-6">
          <div class="w-10 h-px bg-gold"></div>
          <span class="text-gold text-xs tracking-[0.3em] uppercase font-semibold">L'Experiència</span>
          <div class="w-10 h-px bg-gold"></div>
        </div>
        <h2 class="font-serif text-4xl md:text-5xl font-bold text-white">
          Més que un <span class="text-gradient-gold italic">restaurant</span>
        </h2>
      </div>

      <div ref="expCards" class="grid md:grid-cols-3 gap-8">
        <div
          v-for="item in experiences"
          :key="item.title"
          class="group text-center p-8 bg-white/[0.02] border border-white/5 rounded-sm hover:border-gold/20 transition-all duration-500"
        >
          <div class="w-16 h-16 mx-auto mb-6 rounded-full bg-gold/10 flex items-center justify-center group-hover:bg-gold/20 transition-colors duration-500">
            <Icon :icon="item.icon" class="w-7 h-7 text-gold" />
          </div>
          <h3 class="font-serif text-xl font-semibold text-white mb-4 group-hover:text-gold transition-colors duration-300">
            {{ item.title }}
          </h3>
          <p class="text-white/40 text-sm leading-relaxed">{{ item.description }}</p>
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

const expHeader = ref(null)
const expCards = ref(null)

const experiences = [
  {
    icon: 'mdi:candelabra',
    title: 'Ambient',
    description: 'Un espai íntim i elegant al cor de l\'Eixample. Llum càlida, materials nobles i una atmosfera que convida a gaudir de cada moment.',
  },
  {
    icon: 'mdi:leaf',
    title: 'Qualitat',
    description: 'Productes de proximitat seleccionats diàriament als mercats de Barcelona. Del camp i la mar a la teva taula, sense intermediaris.',
  },
  {
    icon: 'mdi:star-outline',
    title: 'Servei',
    description: 'Un equip atent i discret que cuida cada detall. Sommelier dedicat, maridatges personalitzats i atenció a les al·lèrgies i preferències.',
  },
]

onMounted(() => {
  gsap.from(expHeader.value.children, {
    y: 30,
    opacity: 0,
    stagger: 0.1,
    duration: 0.8,
    ease: 'power3.out',
    scrollTrigger: { trigger: expHeader.value, start: 'top 80%' },
  })

  gsap.from(expCards.value.children, {
    y: 50,
    opacity: 0,
    stagger: 0.15,
    duration: 0.8,
    ease: 'power3.out',
    scrollTrigger: { trigger: expCards.value, start: 'top 85%' },
  })
})
</script>
