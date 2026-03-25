<template>
  <footer class="border-t border-white/5 pt-16 pb-8 px-6">
    <div class="max-w-6xl mx-auto">
      <div class="grid sm:grid-cols-2 lg:grid-cols-4 gap-12 mb-16">
        <!-- Brand -->
        <div>
          <div class="flex items-center gap-2 mb-4">
            <span class="font-serif text-2xl font-bold text-gold">Flavor</span>
            <span class="font-serif text-2xl font-light text-white/80">BCN</span>
          </div>
          <p class="text-white/40 text-sm leading-relaxed">
            Cuina mediterrània d'autor al cor de Barcelona. Una experiència gastronòmica única.
          </p>
        </div>

        <!-- Horari -->
        <div>
          <h4 class="font-serif text-sm font-semibold text-gold mb-4 tracking-wider uppercase">Horari</h4>
          <div class="space-y-2 text-sm text-white/40">
            <p>Dilluns: Tancat</p>
            <p>Mar - Diu: 13:30 – 15:30</p>
            <p>Mar - Diu: 20:30 – 23:00</p>
          </div>
        </div>

        <!-- Contacte -->
        <div>
          <h4 class="font-serif text-sm font-semibold text-gold mb-4 tracking-wider uppercase">Contacte</h4>
          <div class="space-y-2 text-sm text-white/40">
            <p>C/ d'Enric Granados, 42</p>
            <p>08008 Barcelona</p>
            <p>+34 933 45 67 89</p>
            <p>hola@flavorbcn.cat</p>
          </div>
        </div>

        <!-- Social -->
        <div>
          <h4 class="font-serif text-sm font-semibold text-gold mb-4 tracking-wider uppercase">Segueix-nos</h4>
          <div class="flex gap-4">
            <a
              v-for="social in socials"
              :key="social.icon"
              href="#"
              class="w-10 h-10 rounded-full bg-white/5 flex items-center justify-center hover:bg-gold/20 hover:text-gold transition-all duration-300 text-white/40"
            >
              <Icon :icon="social.icon" class="w-5 h-5" />
            </a>
          </div>
          <p class="text-white/30 text-xs mt-3">@flavorbcn</p>
        </div>
      </div>

      <!-- Divider -->
      <div class="border-t border-white/5 pt-8 flex flex-col sm:flex-row items-center justify-between gap-4">
        <p class="text-white/20 text-xs">
          &copy; 2026 Flavor BCN. Tots els drets reservats.
        </p>
        <p class="text-white/20 text-xs">
          Fet amb
          <Icon icon="mdi:heart" class="inline w-3 h-3 text-gold/50 mx-1" />
          a Barcelona
        </p>
      </div>
    </div>
  </footer>
</template>

<script setup>
import { Icon } from '@iconify/vue'

const socials = [
  { icon: 'mdi:instagram' },
  { icon: 'mdi:facebook' },
  { icon: 'mdi:twitter' },
]
</script>
