<template>
  <NavBar />

  <section id="sobre-mi" class="home-section home-section--ink pt-2 pb-3 py-md-4">
    <div class="container-fluid px-3 px-md-4 px-lg-5 text-start sobre-mi-scroll-to-vinos mb-2 mb-md-3">
      <a
        href="#packs"
        class="btn-top btn-top--rosa-circle"
        title="Ir a los vinos"
        aria-label="Ir a la sección de vinos y packs"
      >
        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor" viewBox="0 0 16 16" aria-hidden="true">
          <path fill-rule="evenodd" d="M8 4a.5.5 0 0 1 .5.5v5.793l2.146-2.147a.5.5 0 0 1 .708.708l-3 3a.5.5 0 0 1-.708 0l-3-3a.5.5 0 1 1 .708-.708L7.5 10.293V4.5A.5.5 0 0 1 8 4z"/>
        </svg>
      </a>
    </div>
    <div class="container-fluid px-3 px-md-4 px-lg-5 sobre-mi sobre-mi--orbit-stage d-flex flex-column align-items-center justify-content-center">
      <div
        class="sobre-mi-orbit"
        :style="{ '--n': sobreMiFlorCircle.length }"
      >
        <div class="sobre-mi-orbit-core">
          <div class="sobre-mi-texto">
            <p class="mb-0">
              Madre,<br>
              en tus manos todo florece.<br>
              Hoy alzo una copa por tu ternura invencible,<br>
              por tu abrazo que calma cuando la vida tiembla.<br>
              Que nunca falten flores en tu mesa<br>
              ni brindis en tu nombre,<br>
              porque donde estás tú, mamá,<br>
              todo se vuelve luz.
            </p>
          </div>
        </div>
        <figure
          v-for="(flor, i) in sobreMiFlorCircle"
          :key="flor.src"
          class="sobre-mi-orbit-node mb-0"
          :class="{ 'sobre-mi-orbit-node--active': orbitFlorActive === i }"
          :style="{ '--i': i }"
          role="button"
          tabindex="0"
          :aria-pressed="orbitFlorActive === i ? 'true' : 'false'"
          :aria-label="`${flor.alt}. Pulsa para mantener la foto ampliada.`"
          @click="toggleOrbitFlor(i)"
          @keydown.enter.prevent="toggleOrbitFlor(i)"
          @keydown.space.prevent="toggleOrbitFlor(i)"
        >
          <img
            class="sobre-mi-orbit-img"
            :src="flor.src"
            :alt="flor.alt"
            loading="lazy"
            decoding="async"
          >
        </figure>
      </div>
    </div>
    <div class="sobre-mi-cierre">
      Agrega una hermosa flor o ramo de "Flores eternamente bellas" a tu botella de vino o espumante y dale un sello especial a tu regalo.
      <a
        class="sobre-mi-whatsapp text-decoration-none"
        :href="whatsappCatalogoUrl"
        target="_blank"
        rel="noopener noreferrer"
        :class="{ 'opacity-50': !whatsappCatalogoReady }"
        :aria-disabled="!whatsappCatalogoReady"
        aria-label="Solicita tu catálogo de flores, aquí por WhatsApp"
      >
        <span class="sobre-mi-whatsapp-label">Solicita tu catálogo de flores, aquí</span>
        <span
          class="btn btn-whatsapp rounded-circle p-2 shadow-sm d-inline-flex align-items-center justify-content-center sobre-mi-wa-icon flex-shrink-0"
          aria-hidden="true"
        >
          <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor" viewBox="0 0 24 24" aria-hidden="true">
            <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.435 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 00-3.48-8.413z"/>
          </svg>
        </span>
      </a>
    </div>
    <div class="container text-end mt-2">
      <a href="#" class="btn-top btn-top--rosa-circle" title="Volver al inicio" aria-label="Volver al inicio">
        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor" viewBox="0 0 16 16" aria-hidden="true">
          <path d="M8 12a.5.5 0 0 0 .5-.5V5.707l2.146 2.147a.5.5 0 0 0 .708-.708l-3-3a.5.5 0 0 0-.708 0l-3 3a.5.5 0 0 0 .708.708L7.5 5.707V11.5a.5.5 0 0 0 .5.5z"/>
        </svg>
      </a>
    </div>
  </section>
  <section id="packs" class="home-section home-section--slate home-section--madre pt-4 pt-md-5 pb-2 pb-md-3">
    <div class="container text-center packs-header">
      <p class="packs-kicker mb-2">Especial de Vinóloga</p>
      <h3 class="mb-4 fw-bold">Día de la Madre</h3>
    </div>
    <div
      class="packs-carousel-outer d-flex align-items-center gap-2 gap-sm-3 px-2 px-sm-3"
      @mouseenter="pauseCarousel"
      @mouseleave="resumeCarousel"
      @touchstart.passive="onCarouselTouchStart"
      @touchend.passive="onCarouselTouchEnd"
      @focusin="pauseCarousel"
      @focusout="onCarouselFocusOut"
    >
      <button
        type="button"
        class="packs-carousel-arrow packs-carousel-arrow--prev"
        aria-label="Ver packs anteriores"
        @click="scrollCarousel(-1)"
      >
        <svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" fill="currentColor" viewBox="0 0 16 16" aria-hidden="true">
          <path fill-rule="evenodd" d="M11.354 1.646a.5.5 0 0 1 0 .708L5.707 8l5.647 5.646a.5.5 0 0 1-.708.708l-6-6a.5.5 0 0 1 0-.708l6-6a.5.5 0 0 1 .708 0z"/>
        </svg>
      </button>
      <div
        ref="carouselRef"
        class="packs-carousel-wrap flex-grow-1 min-w-0"
        tabindex="0"
        role="region"
        aria-label="Carrusel de packs, desplazamiento horizontal"
      >
        <div class="packs-carousel-inner">
          <div
            v-for="(proyecto, idx) in proyectosLoop"
            :key="`${proyecto.id}-${idx}`"
            class="packs-carousel-slide"
          >
            <CardComponent
              :wine-id="proyecto.id"
              :title="proyecto.vino"
              :winery="proyecto.viña"
              :cepa="proyecto.cepa"
              :valle="proyecto.valle"
              :image="proyecto.image"
              :price="proyecto.price"
              :precio-especial="proyecto.precioEspecial"
            />
          </div>
        </div>
      </div>
      <button
        type="button"
        class="packs-carousel-arrow packs-carousel-arrow--next"
        aria-label="Ver packs siguientes"
        @click="scrollCarousel(1)"
      >
        <svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" fill="currentColor" viewBox="0 0 16 16" aria-hidden="true">
          <path fill-rule="evenodd" d="M4.646 1.646a.5.5 0 0 1 .708 0l6 6a.5.5 0 0 1 0 .708l-6 6a.5.5 0 0 1-.708-.708L10.293 8 4.646 2.354a.5.5 0 0 1 0-.708z"/>
        </svg>
      </button>
    </div>
    <div class="container text-end mt-2">
      <a href="#" class="btn-top btn-top--rosa-circle" title="Volver al inicio" aria-label="Volver al inicio">
        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor" viewBox="0 0 16 16" aria-hidden="true">
          <path d="M8 12a.5.5 0 0 0 .5-.5V5.707l2.146 2.147a.5.5 0 0 0 .708-.708l-3-3a.5.5 0 0 0-.708 0l-3 3a.5.5 0 0 0 .708.708L7.5 5.707V11.5a.5.5 0 0 0 .5.5z"/>
        </svg>
      </a>
    </div>
  </section>

  <div class="prefooter-pitch prefooter-pitch--dark">
    <div class="container text-center">
      <span class="prefooter-line">Otros vinos y packs disponibles</span>
      <span class="prefooter-sep" aria-hidden="true">·</span>
      <span class="prefooter-line">Compra desde 1 botella</span>
      <span class="prefooter-sep" aria-hidden="true">·</span>
      <span class="prefooter-line">Empaques de regalo sin costo</span>
      <span class="prefooter-sep" aria-hidden="true">·</span>
      <span class="prefooter-line">Consulta valor de despacho a tu comuna</span>
    </div>
  </div>

  <div id="contacto" class="contacto-wrap">
    <FooterComponent />
  </div>

</template>

<script setup>
import { computed, onMounted, onUnmounted, ref } from 'vue'
import NavBar from '../components/NavBar'
import FooterComponent from '../components/FooterComponent.vue'
import CardComponent from '../components/CardComponent.vue'
import catalogoPacks from '../data/catalogoPack.json'
import { getWhatsAppCatalogoUrl, isWhatsAppCatalogoConfigured } from '@/config/whatsapp'

/** Dos series iguales para bucle de scroll sin salto visible */
const proyectosLoop = computed(() => [...catalogoPacks, ...catalogoPacks])

const whatsappCatalogoUrl = computed(() => getWhatsAppCatalogoUrl())
const whatsappCatalogoReady = computed(() => isWhatsAppCatalogoConfigured())

/**
 * Variante «órbita»: mismas miniaturas redondas alrededor del poema (orden desde arriba, sentido horario).
 * Nota: en disco está `calas.JPG` (no «cals») y `orquídea.JPG`.
 */
const sobreMiFlorCircle = [
  { src: '/img/calas.JPG', alt: 'Calas' },
  { src: '/img/dalia.jpg', alt: 'Dalia' },
  { src: '/img/gerbera.JPG', alt: 'Gerbera' },
  { src: '/img/girasoles.JPG', alt: 'Girasoles' },
  { src: '/img/lirio_de_agua.JPG', alt: 'Lirio de agua' },
  { src: '/img/margaritas.JPG', alt: 'Margaritas' },
  { src: '/img/orquídea.JPG', alt: 'Orquídea' },
  { src: '/img/ramo_lilium.JPG', alt: 'Ramo de lilium' },
  { src: '/img/ramo_mixto.JPG', alt: 'Ramo mixto' },
]

/** Índice de flor con zoom fijo por clic (null = ninguna). Hover amplía siempre por CSS. */
const orbitFlorActive = ref(null)

function toggleOrbitFlor(i) {
  orbitFlorActive.value = orbitFlorActive.value === i ? null : i
}

const carouselRef = ref(null)
const carouselPaused = ref(false)
const reduceMotion = ref(false)

/** Píxeles por frame (~60 fps); ~0.3 ≈ 18 px/s */
const SCROLL_STEP = 0.32

/** Ancho del hueco del carrusel (sustituye cqi sin container-type, evita avisos del validador CSS) */
const PACKS_CAROUSEL_IW = '--packs-carousel-iw'

let rafId = 0
let syncCarouselRaf = null
let touchResumeTimer = null
let focusResumeTimer = null
let arrowResumeTimer = null
let carouselResizeObserver = null

function syncCarouselInlineSize() {
  const el = carouselRef.value
  if (!el) return
  const w = el.clientWidth
  if (w > 0) el.style.setProperty(PACKS_CAROUSEL_IW, `${w}px`)
}

/**
 * ResizeObserver + setProperty en el mismo frame puede disparar
 * "ResizeObserver loop completed with undelivered notifications".
 * Se aplaza al siguiente paint (rAF).
 */
function scheduleSyncCarouselInlineSize() {
  if (syncCarouselRaf != null) return
  syncCarouselRaf = requestAnimationFrame(() => {
    syncCarouselRaf = null
    syncCarouselInlineSize()
  })
}

function pauseCarousel() {
  carouselPaused.value = true
}

function resumeCarousel() {
  carouselPaused.value = false
}

function onCarouselTouchStart() {
  pauseCarousel()
  if (touchResumeTimer) {
    clearTimeout(touchResumeTimer)
    touchResumeTimer = null
  }
}

function onCarouselTouchEnd() {
  if (touchResumeTimer) clearTimeout(touchResumeTimer)
  touchResumeTimer = setTimeout(() => {
    carouselPaused.value = false
    touchResumeTimer = null
  }, 2400)
}

function onCarouselFocusOut(ev) {
  const outer = ev.currentTarget
  const next = ev.relatedTarget
  if (next && outer.contains(next)) return
  if (focusResumeTimer) clearTimeout(focusResumeTimer)
  focusResumeTimer = setTimeout(() => {
    carouselPaused.value = false
    focusResumeTimer = null
  }, 400)
}

function scrollCarousel(direction) {
  const el = carouselRef.value
  if (!el) return
  pauseCarousel()
  if (arrowResumeTimer) clearTimeout(arrowResumeTimer)

  const inner = el.querySelector('.packs-carousel-inner')
  const firstSlide = inner?.querySelector('.packs-carousel-slide')
  let delta = el.clientWidth * direction
  if (inner && firstSlide) {
    const gapPx = parseFloat(getComputedStyle(inner).gap) || 0
    const slideW = firstSlide.offsetWidth
    const threeCols = window.matchMedia('(min-width: 768px)').matches
    /* Móvil: un avance = 1 tarjeta + hueco; desktop: el viewport ya encaja 3 enteras */
    if (!threeCols) delta = (slideW + gapPx) * direction
  }

  el.scrollBy({
    left: delta,
    behavior: reduceMotion.value ? 'auto' : 'smooth',
  })
  arrowResumeTimer = setTimeout(() => {
    carouselPaused.value = false
    arrowResumeTimer = null
  }, 3200)
}

function tick() {
  const el = carouselRef.value
  if (el && !carouselPaused.value && !reduceMotion.value) {
    const half = el.scrollWidth / 2
    if (half > 1) {
      el.scrollLeft += SCROLL_STEP
      if (el.scrollLeft >= half) {
        el.scrollLeft -= half
      }
    }
  }
  rafId = requestAnimationFrame(tick)
}

onMounted(() => {
  reduceMotion.value = window.matchMedia('(prefers-reduced-motion: reduce)').matches
  syncCarouselInlineSize()
  const el = carouselRef.value
  if (el && typeof ResizeObserver !== 'undefined') {
    carouselResizeObserver = new ResizeObserver(() => scheduleSyncCarouselInlineSize())
    carouselResizeObserver.observe(el)
  }
  rafId = requestAnimationFrame(tick)
})

onUnmounted(() => {
  if (syncCarouselRaf != null) {
    cancelAnimationFrame(syncCarouselRaf)
    syncCarouselRaf = null
  }
  carouselResizeObserver?.disconnect()
  carouselResizeObserver = null
  cancelAnimationFrame(rafId)
  if (touchResumeTimer) clearTimeout(touchResumeTimer)
  if (focusResumeTimer) clearTimeout(focusResumeTimer)
  if (arrowResumeTimer) clearTimeout(arrowResumeTimer)
})

</script>

<style scoped>
.home-section {
  background-color: var(--vin-negro-marca);
  background-image: var(--vin-bg-atmosfera);
  background-repeat: no-repeat;
  background-size: cover;
}

.home-section--ink {
  background-color: var(--vin-negro-marca);
  background-image: var(--vin-bg-atmosfera);
  background-repeat: no-repeat;
  background-size: cover;
}

.home-section--slate {
  background-color: var(--vin-fondo-packs);
  background-image:
    radial-gradient(circle at 12% 18%, rgba(var(--vin-leche-rgb), 0.26), transparent 46%),
    radial-gradient(circle at 88% 76%, rgba(var(--vin-pastel-nube-rgb), 0.32), transparent 44%),
    radial-gradient(circle at 46% 6%, rgba(var(--vin-rosa-melocoton-rgb), 0.2), transparent 38%),
    radial-gradient(ellipse 82% 58% at 50% 102%, rgba(var(--vin-rosa-ballet-rgb), 0.22), transparent 52%),
    radial-gradient(circle at 72% 42%, rgba(var(--vin-rosa-sorbete-rgb), 0.12), transparent 36%);
  background-repeat: no-repeat;
  background-size: cover;
}

.home-section--madre {
  background:
    radial-gradient(circle at 8% 0%, rgba(var(--vin-leche-rgb), 0.36), transparent 36%),
    radial-gradient(circle at 86% 12%, rgba(var(--vin-pastel-nube-rgb), 0.4), transparent 38%),
    radial-gradient(circle at 50% 118%, rgba(var(--vin-pastel-polvo-rgb), 0.22), transparent 48%),
    radial-gradient(circle at 26% 58%, rgba(var(--vin-rosa-cuarzo-rgb), 0.22), transparent 44%),
    radial-gradient(circle at 94% 46%, rgba(var(--vin-rosa-sorbete-rgb), 0.18), transparent 40%),
    radial-gradient(ellipse 70% 45% at 52% 22%, rgba(var(--vin-rosa-melocoton-rgb), 0.14), transparent 50%),
    linear-gradient(165deg, #352f34 0%, #3e363e 36%, #3a323a 58%, #30292f 100%);
}

.packs-header {
  position: relative;
  padding-bottom: 0.75rem;
}

.packs-kicker {
  margin: 0;
  color: var(--vin-rosa-texto-brillo);
  text-transform: uppercase;
  letter-spacing: 0.14em;
  font-size: 0.66rem;
  font-weight: 800;
}

@supports (-webkit-background-clip: text) or (background-clip: text) {
  .packs-kicker {
    background-image: linear-gradient(
      105deg,
      #fff9fc 0%,
      #fcdbe9 32%,
      #f8c9dc 48%,
      #ffeef6 100%
    );
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
  }
}

.home-divider {
  max-width: min(100%, 960px);
  margin-left: auto;
  margin-right: auto;
  opacity: 0.35;
}

/* Misma base que el footer: evita cualquier rendija entre prefooter y pie */
.contacto-wrap {
  margin: 0;
  padding: 0;
  background-color: var(--vin-superficie-oscura);
}

.prefooter-pitch {
  padding-top: 0.85rem;
  padding-bottom: 1.35rem;
  margin-bottom: 0;
}

.prefooter-pitch .container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  row-gap: 0.45rem;
  column-gap: 0.25rem;
}

/* Mismo fondo y ribete que la navbar (.bg-vin-negro + .nav-vino) */
.prefooter-pitch--dark {
  width: 100%;
  margin-inline: 0;
  background-color: var(--vin-negro-marca);
  background-image: none;
  border-top: 1px solid var(--vin-borde-sutil);
  border-bottom: none;
  box-shadow: 0 1px 0 0 rgba(var(--vin-pastel-polvo-rgb), 0.45);
}

.prefooter-line {
  font-size: clamp(0.84rem, 2.25vw, 1rem);
  line-height: 1.55;
  font-weight: 500;
  letter-spacing: 0.025em;
  color: var(--vin-texto-claro);
}

.prefooter-sep {
  color: #a85268;
  text-shadow: none;
  font-weight: 800;
  font-size: 1.65em;
  line-height: 1;
  padding-inline: 0.32rem;
  user-select: none;
}

/* Móvil: una línea por texto, sin separadores */
@media (max-width: 575.98px) {
  .prefooter-pitch .container {
    flex-direction: column;
    flex-wrap: nowrap;
    align-items: center;
    row-gap: 0.45rem;
    column-gap: 0;
  }

  .prefooter-sep {
    display: none;
  }
}

.home-section h3 {
  font-family: 'Nunito', system-ui, sans-serif;
  font-size: clamp(1.3rem, 4vw, 1.9rem);
  letter-spacing: 0.02em;
  display: inline-block;
  position: relative;
  padding: 0.2em 0.85em 1rem;
  margin-bottom: 0.4rem;
  z-index: 0;
  /* Fallback si el navegador no aplica background-clip en texto */
  color: #fcdbe9;
  text-shadow:
    0 0 24px rgba(var(--vin-rosa-sorbete-rgb), 0.65),
    0 0 52px rgba(var(--vin-rosa-ballet-rgb), 0.35),
    0 1px 2px rgba(58, 15, 24, 0.45);
}

@supports (-webkit-background-clip: text) or (background-clip: text) {
  .home-section h3 {
    background-image: var(--vin-titulo-seccion-fill);
    background-size: 140% 140%;
    background-position: 30% 45%;
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
    -webkit-text-fill-color: transparent;
    text-shadow: none;
  }

  .home-section h3::selection {
    background: rgba(var(--vin-rosa-sorbete-rgb), 0.45);
    color: var(--vin-profundo);
    -webkit-text-fill-color: var(--vin-profundo);
    background-clip: border-box;
    -webkit-background-clip: border-box;
  }
}

/*
 * Línea tipo viña bajo el título (CSS):
 * ::before = tallo en curva (cuarto de elipse con bordes).
 * ::after  = “hojas” (elipses + box-shadow) y un puntito tipo uva.
 */
.home-section h3::before {
  content: '';
  position: absolute;
  z-index: -1;
  left: 50%;
  bottom: 0.18rem;
  width: clamp(2.35rem, 14vw, 3.15rem);
  height: clamp(1.1rem, 5.5vw, 1.45rem);
  transform: translateX(calc(-50% - 0.12rem)) rotate(-13deg);
  transform-origin: 0 100%;
  border: none;
  border-bottom: 2.5px solid var(--vin-titulo-tallo);
  border-left: 2.5px solid var(--vin-titulo-tallo);
  border-radius: 0 0 0 100%;
  background: transparent;
  opacity: 0.82;
  pointer-events: none;
}

/* Franja bajo el título: tonos cálidos (rosa / coral / champagne), acorde al Día de la Madre */
.home-section h3::after {
  content: '';
  position: absolute;
  z-index: 0;
  left: 50%;
  bottom: 0.12rem;
  width: clamp(2.5rem, 18vw, 3.75rem);
  height: 3px;
  transform: translateX(-50%);
  border-radius: 999px;
  pointer-events: none;
  background: var(--vin-titulo-subrayado);
  box-shadow:
    0 1px 6px rgba(var(--vin-pastel-polvo-rgb), 0.45),
    0 0 16px rgba(var(--vin-rosa-sorbete-rgb), 0.35),
    0 0 26px rgba(var(--vin-rosa-melocoton-rgb), 0.22);
  opacity: 0.96;
}

@media (prefers-reduced-motion: no-preference) {
  .home-section h3::before {
    animation: homeTituloVinaTallo 5s ease-in-out infinite;
  }

  .home-section h3::after {
    animation: homeTituloVinaHojas 5s ease-in-out infinite;
  }
}

@keyframes homeTituloVinaTallo {
  0%,
  100% {
    transform: translateX(calc(-50% - 0.12rem)) rotate(-13deg);
  }
  50% {
    transform: translateX(calc(-50% - 0.06rem)) rotate(-10deg);
  }
}

@keyframes homeTituloVinaHojas {
  0%,
  100% {
    transform: translateX(-50%) scaleX(1);
    opacity: 0.86;
  }
  50% {
    transform: translateX(-50%) scaleX(1.05);
    opacity: 0.96;
  }
}

@media (prefers-reduced-motion: reduce) {
  .home-section h3::before,
  .home-section h3::after {
    animation: none !important;
  }
}

/* Título de bloque: separación respecto al degradado / halo del fondo */
#sobre-mi > h3 {
  filter: drop-shadow(0 3px 18px rgba(8, 5, 9, 0.72));
}

#sobre-mi .sobre-mi-texto {
  flex: 0 1 auto;
  min-width: 0;
  max-width: min(100%, 62rem);
  text-align: justify;
  line-height: 1.78;
  font-size: clamp(0.96rem, 2vw, 1.16rem);
  font-weight: 500;
  font-family: "Palatino Linotype", "Book Antiqua", Palatino, Georgia, serif;
  font-style: italic;
  color: #fdfdfd;
  text-shadow:
    0 1px 2px rgba(12, 8, 11, 0.92),
    0 2px 18px rgba(8, 5, 8, 0.65);
}

/* Órbita circular: miniaturas iguales y redondas alrededor del poema */
#sobre-mi .sobre-mi--orbit-stage {
  padding-block: clamp(0.75rem, 3vw, 1.5rem);
}

#sobre-mi .sobre-mi-orbit {
  position: relative;
  width: min(100%, 560px);
  aspect-ratio: 1;
  margin-inline: auto;
  flex-shrink: 0;
  overflow: visible;
  /* Referencia para unidades cqi/cqb (radio basado en el ancho real del órbita) */
  container-type: inline-size;
  container-name: orbit-sobre-mi;
  --sobre-orbit-thumb: clamp(52px, 12.5vw, 82px);
  /*
   * Radio máximo seguro: centro de la miniatura a mitad del lado del cuadrado,
   * menos radio de la foto y un margen (evita solapamiento con el poema en móvil).
   */
  --sobre-orbit-r: min(37vw, 214px);
  --sobre-orbit-zoom: 1.52;
}

@supports (width: 1cqi) {
  #sobre-mi .sobre-mi-orbit {
    --sobre-orbit-r: calc(
      50cqi - var(--sobre-orbit-thumb) / 2 - clamp(8px, 2.5cqi, 14px)
    );
  }
}

@media (min-width: 576px) {
  #sobre-mi .sobre-mi-orbit {
    --sobre-orbit-thumb: clamp(58px, 11.5vw, 88px);
  }
}

@media (min-width: 992px) {
  #sobre-mi .sobre-mi-orbit {
    width: min(100%, 600px);
    --sobre-orbit-thumb: 88px;
  }
}

/* Móvil / portrait estrecho: poema más compacto, flores más pequeñas, menos zoom, texto siempre encima */
@media (max-width: 767.98px) {
  #sobre-mi .sobre-mi-orbit {
    --sobre-orbit-thumb: clamp(34px, 8.5vw, 44px);
    --sobre-orbit-zoom: 1.35;
  }

  #sobre-mi .sobre-mi-orbit-core {
    z-index: 8;
  }

  #sobre-mi .sobre-mi-orbit-core .sobre-mi-texto {
    max-width: min(52%, 11rem);
    font-size: clamp(0.78rem, 3.35vw, 0.92rem);
    line-height: 1.52;
    padding-inline: 0.2rem;
  }
}

@media (max-width: 399.98px) {
  #sobre-mi .sobre-mi-orbit {
    --sobre-orbit-thumb: clamp(30px, 7.8vw, 40px);
    --sobre-orbit-zoom: 1.28;
  }

  #sobre-mi .sobre-mi-orbit-core .sobre-mi-texto {
    max-width: min(48%, 10rem);
    font-size: clamp(0.74rem, 3.2vw, 0.86rem);
    line-height: 1.48;
  }
}

#sobre-mi .sobre-mi-orbit-core {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 2;
  pointer-events: none;
}

#sobre-mi .sobre-mi-orbit-core .sobre-mi-texto {
  pointer-events: auto;
  max-width: min(74%, 17rem);
  text-align: center;
  position: relative;
  z-index: 3;
}

#sobre-mi .sobre-mi-orbit-node {
  position: absolute;
  left: 50%;
  top: 50%;
  z-index: 1;
  width: var(--sobre-orbit-thumb);
  height: var(--sobre-orbit-thumb);
  margin: 0;
  transform-origin: center center;
  /* Centrar en el eje del poema y situar en la circunferencia (no usar margin negativo + margin: 0 a la vez) */
  transform: translate(-50%, -50%) rotate(calc(var(--i) * 360deg / var(--n)))
    translateY(calc(-1 * var(--sobre-orbit-r))) rotate(calc(-360deg * var(--i) / var(--n)));
  padding: 0;
  border: none;
  background: transparent;
  cursor: pointer;
  outline-offset: 4px;
  border-radius: 50%;
}

#sobre-mi .sobre-mi-orbit-node:focus-visible {
  outline: 2px solid rgba(var(--vin-rosa-sorbete-rgb), 0.75);
}

#sobre-mi .sobre-mi-orbit-node:hover,
#sobre-mi .sobre-mi-orbit-node:focus-visible,
#sobre-mi .sobre-mi-orbit-node--active {
  z-index: 4;
}

@media (min-width: 768px) {
  #sobre-mi .sobre-mi-orbit-node:hover,
  #sobre-mi .sobre-mi-orbit-node:focus-visible,
  #sobre-mi .sobre-mi-orbit-node--active {
    z-index: 12;
  }
}

#sobre-mi .sobre-mi-orbit-img {
  display: block;
  width: 100%;
  height: 100%;
  position: relative;
  object-fit: cover;
  border-radius: 50%;
  border: 2px solid rgba(255, 214, 232, 0.42);
  box-shadow:
    0 6px 18px rgba(8, 5, 9, 0.42),
    0 0 0 1px rgba(255, 236, 245, 0.18);
  transition:
    transform 0.24s ease,
    box-shadow 0.24s ease,
    border-color 0.24s ease;
}

#sobre-mi .sobre-mi-orbit-node:hover .sobre-mi-orbit-img,
#sobre-mi .sobre-mi-orbit-node:focus-visible .sobre-mi-orbit-img,
#sobre-mi .sobre-mi-orbit-node--active .sobre-mi-orbit-img {
  transform: scale(var(--sobre-orbit-zoom));
  border-color: rgba(255, 236, 245, 0.65);
  box-shadow:
    0 12px 28px rgba(8, 5, 9, 0.48),
    0 0 0 2px rgba(var(--vin-rosa-sorbete-rgb), 0.35);
}

@media (prefers-reduced-motion: reduce) {
  #sobre-mi .sobre-mi-orbit-img {
    transition: border-color 0.15s ease, box-shadow 0.15s ease;
  }

  #sobre-mi .sobre-mi-orbit-node:hover .sobre-mi-orbit-img,
  #sobre-mi .sobre-mi-orbit-node:focus-visible .sobre-mi-orbit-img,
  #sobre-mi .sobre-mi-orbit-node--active .sobre-mi-orbit-img {
    transition: none;
  }
}

#sobre-mi .sobre-mi-cierre {
  width: 100%;
  margin-top: 1rem;
  padding: 0.8rem clamp(1rem, 4vw, 3rem);
  text-align: center;
  font-size: clamp(0.95rem, 2.2vw, 1.12rem);
  line-height: 1.5;
  color: #ffeaf4;
  background: linear-gradient(
    90deg,
    rgba(255, 214, 232, 0.12),
    rgba(255, 214, 232, 0.22),
    rgba(255, 214, 232, 0.12)
  );
  border-top: 1px solid rgba(255, 214, 232, 0.28);
  border-bottom: 1px solid rgba(255, 214, 232, 0.28);
}

#sobre-mi .sobre-mi-whatsapp {
  margin-top: 0.65rem;
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  color: #ffffff;
  text-decoration: none;
  font-weight: 600;
}

#sobre-mi .sobre-mi-whatsapp .sobre-mi-wa-icon {
  line-height: 1;
  pointer-events: none;
}

#sobre-mi .sobre-mi-whatsapp:hover .sobre-mi-whatsapp-label,
#sobre-mi .sobre-mi-whatsapp:focus-visible .sobre-mi-whatsapp-label {
  text-decoration: underline;
  color: #d9ffd9;
}

#sobre-mi .sobre-mi-whatsapp:hover .btn-whatsapp,
#sobre-mi .sobre-mi-whatsapp:focus-visible .btn-whatsapp {
  filter: brightness(1.06);
}

#sobre-mi .sobre-mi-whatsapp:focus-visible {
  outline: 2px solid rgba(var(--vin-rosa-sorbete-rgb), 0.55);
  outline-offset: 4px;
  border-radius: 0.35rem;
}

/* Rosa vivo legible: luminancia alta + sombras oscuras (igual que antes) */
#sobre-mi .sobre-mi-vino-mayus {
  color: #ffd6e8;
  font-weight: 800;
  letter-spacing: 0.045em;
  text-shadow:
    0 1px 3px rgba(14, 10, 12, 0.98),
    0 2px 4px rgba(8, 5, 9, 0.92),
    0 0 22px rgba(var(--vin-rosa-sorbete-rgb), 0.42),
    0 0 3px rgba(58, 15, 24, 0.85);
}

.highlight {
  color: var(--vin-acento);
  font-style: italic;
  font-weight: bold;
}

.frase-final {
  font-style: italic;
  animation: colorPulse 3s ease-in-out infinite;
}

@keyframes colorPulse {
  0% {
    color: var(--vin-texto-muted);
  }
  50% {
    color: var(--vin-acento);
  }
  100% {
    color: var(--vin-texto-muted);
  }
}

.btn-top {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  line-height: 1;
}

.btn-top--rosa-circle {
  width: clamp(2.35rem, 7vw, 2.65rem);
  height: clamp(2.35rem, 7vw, 2.65rem);
  padding: 0;
  border: none;
  border-radius: 50%;
  background-image: var(--vin-btn-carousel-fill);
  box-shadow: var(--vin-btn-carousel-shadow);
  color: #fff !important;
  text-decoration: none;
  cursor: pointer;
  transition:
    filter 0.2s ease,
    transform 0.15s ease,
    box-shadow 0.2s ease;
}

.btn-top--rosa-circle:hover {
  filter: brightness(1.06) saturate(1.08);
  box-shadow: var(--vin-btn-carousel-shadow-hover);
  color: #fff !important;
}

.btn-top--rosa-circle:active {
  filter: brightness(0.92);
  transform: scale(0.96);
}

.btn-top--rosa-circle:focus-visible {
  outline: 2px solid rgba(var(--vin-acento-rgb), 0.55);
  outline-offset: 3px;
}

.btn-top--rosa-circle svg {
  flex-shrink: 0;
}

.packs-carousel-outer {
  max-width: 100%;
  min-height: 0;
}

.packs-carousel-arrow {
  flex-shrink: 0;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: clamp(2.5rem, 8vw, 2.85rem);
  height: clamp(2.5rem, 8vw, 2.85rem);
  padding: 0;
  border: none;
  border-radius: 50%;
  background-image: var(--vin-btn-carousel-fill);
  color: #fff;
  box-shadow: var(--vin-btn-carousel-shadow);
  cursor: pointer;
  transition:
    filter 0.2s ease,
    transform 0.15s ease,
    box-shadow 0.2s ease;
}

.packs-carousel-arrow:hover {
  filter: brightness(1.06) saturate(1.08);
  box-shadow: var(--vin-btn-carousel-shadow-hover);
}

.packs-carousel-arrow:active {
  filter: brightness(0.92);
  transform: scale(0.96);
}

.packs-carousel-arrow:focus-visible {
  outline: 2px solid rgba(var(--vin-acento-rgb), 0.55);
  outline-offset: 3px;
}

.packs-carousel-wrap {
  overflow-x: auto;
  overflow-y: hidden;
  scroll-snap-type: x mandatory;
  -webkit-overflow-scrolling: touch;
  scrollbar-width: thin;
  scrollbar-color: rgba(var(--vin-rosa-ballet-rgb), 0.42) transparent;
  padding-block: 0.25rem 0.75rem;
  outline: none;
}

.packs-carousel-wrap:focus-visible {
  box-shadow: 0 0 0 2px rgba(var(--vin-acento-rgb), 0.35);
  border-radius: 0.35rem;
}

.packs-carousel-wrap::-webkit-scrollbar {
  height: 6px;
}

.packs-carousel-wrap::-webkit-scrollbar-thumb {
  background: linear-gradient(
    180deg,
    rgba(var(--vin-pastel-nube-rgb), 0.65),
    rgba(var(--vin-rosa-sorbete-rgb), 0.55)
  );
  border-radius: 4px;
}

.packs-carousel-inner {
  --packs-gap: clamp(0.75rem, 2vw, 1.15rem);
  display: flex;
  flex-direction: row;
  align-items: stretch;
  gap: var(--packs-gap);
  width: max-content;
  min-height: 100%;
}

/*
 * Siempre tarjetas enteras en el viewport: 1 columna en móvil, 3 en md+.
 * --packs-carousel-iw = ancho del área scroll (ResizeObserver).
 */
.packs-carousel-slide {
  flex: 0 0 auto;
  box-sizing: border-box;
  scroll-snap-align: start;
  scroll-snap-stop: normal;
  min-height: 0;
  width: var(--packs-carousel-iw, 100%);
  display: flex;
  flex-direction: column;
}

@media (min-width: 768px) {
  .packs-carousel-slide {
    width: calc((var(--packs-carousel-iw, 100%) - 2 * var(--packs-gap)) / 3);
  }
}

.packs-carousel-slide > * {
  flex: 1 1 auto;
  width: 100%;
  min-height: 0;
  align-self: stretch;
}
</style>