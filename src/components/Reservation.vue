<template>
  <section id="reserva" class="py-24 px-6 relative">
    <div class="max-w-6xl mx-auto">
      <div ref="resHeader" class="text-center mb-16">
        <div class="flex items-center justify-center gap-3 mb-6">
          <div class="w-10 h-px bg-gold"></div>
          <Icon icon="mdi:calendar-clock" class="text-gold w-5 h-5" />
          <div class="w-10 h-px bg-gold"></div>
        </div>
        <h2 class="font-serif text-4xl md:text-5xl font-bold text-white mb-4">Reserva</h2>
        <p class="text-white/50 italic font-serif">Fes la teva reserva i vine a gaudir</p>
      </div>

      <div ref="resContent" class="grid md:grid-cols-5 gap-12">
        <!-- Form -->
        <form class="md:col-span-3 space-y-5" @submit.prevent="handleSubmit">
          <div class="grid sm:grid-cols-2 gap-5">
            <div>
              <label class="block text-xs text-white/40 tracking-wider mb-2 uppercase">Nom</label>
              <input
                v-model="form.name"
                type="text"
                placeholder="El teu nom"
                class="w-full bg-white/[0.04] border border-white/10 rounded-sm px-4 py-3 text-white placeholder-white/20 focus:border-gold/50 focus:outline-none transition-colors"
              />
            </div>
            <div>
              <label class="block text-xs text-white/40 tracking-wider mb-2 uppercase">Email</label>
              <input
                v-model="form.email"
                type="email"
                placeholder="email@exemple.com"
                class="w-full bg-white/[0.04] border border-white/10 rounded-sm px-4 py-3 text-white placeholder-white/20 focus:border-gold/50 focus:outline-none transition-colors"
              />
            </div>
          </div>

          <div class="grid sm:grid-cols-3 gap-5">
            <div>
              <label class="block text-xs text-white/40 tracking-wider mb-2 uppercase">Data</label>
              <input
                v-model="form.date"
                type="date"
                class="w-full bg-white/[0.04] border border-white/10 rounded-sm px-4 py-3 text-white focus:border-gold/50 focus:outline-none transition-colors"
              />
            </div>
            <div>
              <label class="block text-xs text-white/40 tracking-wider mb-2 uppercase">Hora</label>
              <select
                v-model="form.time"
                class="w-full bg-white/[0.04] border border-white/10 rounded-sm px-4 py-3 text-white focus:border-gold/50 focus:outline-none transition-colors"
              >
                <option value="" disabled class="bg-dark">Selecciona</option>
                <option value="13:30" class="bg-dark">13:30</option>
                <option value="14:00" class="bg-dark">14:00</option>
                <option value="14:30" class="bg-dark">14:30</option>
                <option value="20:30" class="bg-dark">20:30</option>
                <option value="21:00" class="bg-dark">21:00</option>
                <option value="21:30" class="bg-dark">21:30</option>
                <option value="22:00" class="bg-dark">22:00</option>
              </select>
            </div>
            <div>
              <label class="block text-xs text-white/40 tracking-wider mb-2 uppercase">Comensals</label>
              <select
                v-model="form.guests"
                class="w-full bg-white/[0.04] border border-white/10 rounded-sm px-4 py-3 text-white focus:border-gold/50 focus:outline-none transition-colors"
              >
                <option v-for="n in 10" :key="n" :value="n" class="bg-dark">{{ n }} {{ n === 1 ? 'persona' : 'persones' }}</option>
              </select>
            </div>
          </div>

          <div>
            <label class="block text-xs text-white/40 tracking-wider mb-2 uppercase">Missatge (opcional)</label>
            <textarea
              v-model="form.message"
              rows="3"
              placeholder="Al·lèrgies, preferències, celebracions..."
              class="w-full bg-white/[0.04] border border-white/10 rounded-sm px-4 py-3 text-white placeholder-white/20 focus:border-gold/50 focus:outline-none transition-colors resize-none"
            ></textarea>
          </div>

          <button
            type="submit"
            class="w-full py-4 bg-gold text-dark font-semibold tracking-widest text-sm hover:bg-gold-light transition-all duration-300 rounded-sm"
          >
            CONFIRMAR RESERVA
          </button>
        </form>

        <!-- Contact info -->
        <div class="md:col-span-2 space-y-8">
          <div class="p-6 bg-white/[0.02] border border-white/5 rounded-sm">
            <h3 class="font-serif text-lg font-semibold text-gold mb-4">Informació</h3>
            <div class="space-y-4">
              <div class="flex items-start gap-3">
                <Icon icon="mdi:map-marker" class="text-gold w-5 h-5 mt-0.5 shrink-0" />
                <div>
                  <p class="text-white/80 text-sm">Carrer d'Enric Granados, 42</p>
                  <p class="text-white/40 text-xs">08008 Barcelona</p>
                </div>
              </div>
              <div class="flex items-start gap-3">
                <Icon icon="mdi:phone" class="text-gold w-5 h-5 mt-0.5 shrink-0" />
                <p class="text-white/80 text-sm">+34 933 45 67 89</p>
              </div>
              <div class="flex items-start gap-3">
                <Icon icon="mdi:email-outline" class="text-gold w-5 h-5 mt-0.5 shrink-0" />
                <p class="text-white/80 text-sm">reserva@flavorbcn.cat</p>
              </div>
            </div>
          </div>

          <div class="p-6 bg-white/[0.02] border border-white/5 rounded-sm">
            <h3 class="font-serif text-lg font-semibold text-gold mb-4">Horari</h3>
            <div class="space-y-2 text-sm">
              <div class="flex justify-between">
                <span class="text-white/40">Dilluns</span>
                <span class="text-white/60">Tancat</span>
              </div>
              <div class="flex justify-between">
                <span class="text-white/40">Dimarts - Diumenge</span>
                <span class="text-white/60">13:30 – 15:30</span>
              </div>
              <div class="flex justify-between">
                <span class="text-white/40"></span>
                <span class="text-white/60">20:30 – 23:00</span>
              </div>
            </div>
          </div>
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

const resHeader = ref(null)
const resContent = ref(null)

const form = ref({
  name: '',
  email: '',
  date: '',
  time: '',
  guests: 2,
  message: '',
})

function handleSubmit() {
  alert('Gràcies! La teva reserva ha estat enviada. Et confirmarem per email.')
}

onMounted(() => {
  gsap.from(resHeader.value.children, {
    y: 30,
    opacity: 0,
    stagger: 0.1,
    duration: 0.8,
    ease: 'power3.out',
    scrollTrigger: { trigger: resHeader.value, start: 'top 80%' },
  })

  gsap.from(resContent.value.children, {
    y: 40,
    opacity: 0,
    stagger: 0.2,
    duration: 0.8,
    ease: 'power3.out',
    scrollTrigger: { trigger: resContent.value, start: 'top 85%' },
  })
})
</script>
