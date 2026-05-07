<template>
  <NavBar />

  <section id="sobre-mi" class="home-section home-section--ink py-3 py-md-4">
    <h3 class="mb-2 mb-md-3 fw-bold">El mundo de Vinóloga</h3>
    <div class="container sobre-mi d-flex flex-column flex-md-row align-items-center justify-content-center gap-3">
      <div
        ref="sobreMiFotoShellRef"
        class="sobre-mi-foto-shell"
        :class="{ 'sobre-mi-foto-shell--in-view': sobreMiFotoInView }"
      >
        <div class="sobre-mi-foto-marco" aria-hidden="true" />
        <div class="sobre-mi-foto">
          <img
            class="sobre-mi-foto__img"
            :src="sobreMiFotoSrc"
            alt="Logo Vinóloga"
            width="400"
            height="400"
            loading="lazy"
            decoding="async"
          >
        </div>
      </div>
      <div class="sobre-mi-texto">
        <p class="mb-1 mb-md-2">
          Es tiempo de <span class="sobre-mi-vino-mayus">APRENDER</span>, es tiempo de
          <span class="sobre-mi-vino-mayus">COMPARTIR</span>, es tiempo de
          <span class="sobre-mi-vino-mayus">DISFRUTAR</span>.
        </p>
        <p class="mb-0">
          Bienvenido al Mundo de Vinóloga...el mundo de los "<span class="sobre-mi-vino-mayus">VINOS CON CUENTO</span>"...
        </p>
      </div>
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
      <p class="packs-kicker mb-2">Especial</p>
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

/** Logo en `public/img/logo-vinologa.png` */
const sobreMiFotoSrc = '/img/logo-vinologa.png'

/** Dos series iguales para bucle de scroll sin salto visible */
const proyectosLoop = computed(() => [...catalogoPacks, ...catalogoPacks])

const carouselRef = ref(null)
const sobreMiFotoShellRef = ref(null)
const sobreMiFotoInView = ref(false)
const carouselPaused = ref(false)
const reduceMotion = ref(false)

let sobreMiFotoObserver = null

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

function setupSobreMiFotoReveal() {
  if (reduceMotion.value) {
    sobreMiFotoInView.value = true
    return
  }
  const shell = sobreMiFotoShellRef.value
  if (!shell) {
    sobreMiFotoInView.value = true
    return
  }
  if (typeof IntersectionObserver === 'undefined') {
    sobreMiFotoInView.value = true
    return
  }
  sobreMiFotoObserver = new IntersectionObserver(
    (entries) => {
      for (const entry of entries) {
        if (entry.isIntersecting) {
          sobreMiFotoInView.value = true
          sobreMiFotoObserver?.unobserve(entry.target)
        }
      }
    },
    { threshold: 0.22, rootMargin: '0px 0px -8% 0px' },
  )
  sobreMiFotoObserver.observe(shell)
}

onMounted(() => {
  reduceMotion.value = window.matchMedia('(prefers-reduced-motion: reduce)').matches
  setupSobreMiFotoReveal()
  syncCarouselInlineSize()
  const el = carouselRef.value
  if (el && typeof ResizeObserver !== 'undefined') {
    carouselResizeObserver = new ResizeObserver(() => scheduleSyncCarouselInlineSize())
    carouselResizeObserver.observe(el)
  }
  rafId = requestAnimationFrame(tick)
})

onUnmounted(() => {
  sobreMiFotoObserver?.disconnect()
  sobreMiFotoObserver = null
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

#sobre-mi .sobre-mi-foto-shell {
  --foto-tam: 184px;
  flex: 0 0 auto;
  width: var(--foto-tam);
  height: var(--foto-tam);
  margin-inline: auto;
  position: relative;
  opacity: 0;
  transform: scale(0.96) translateY(14px);
  transition:
    opacity 0.8s cubic-bezier(0.22, 1, 0.36, 1),
    transform 0.8s cubic-bezier(0.22, 1, 0.36, 1);
}

#sobre-mi .sobre-mi-foto-shell--in-view {
  opacity: 1;
  transform: scale(1) translateY(0);
}

.sobre-mi-foto-marco {
  position: absolute;
  inset: -4px;
  border-radius: 50%;
  z-index: 0;
  background: conic-gradient(
    from 0deg,
    #c9a227,
    #3ddc84,
    #4dabf7,
    #9775fa,
    #f783ac,
    rgba(var(--vin-acento-rgb), 0.95),
    #c9a227
  );
  animation: sobreMiMarcoGiro 12s linear infinite;
}

@keyframes sobreMiMarcoGiro {
  to {
    transform: rotate(360deg);
  }
}

#sobre-mi .sobre-mi-foto {
  position: absolute;
  inset: 3px;
  z-index: 1;
  border-radius: 50%;
  overflow: hidden;
  background-color: var(--vin-negro-marca);
  box-shadow:
    0 0 0 2px rgba(255, 255, 255, 0.1),
    0 12px 36px rgba(0, 0, 0, 0.45);
}

@media (min-width: 768px) {
  #sobre-mi .sobre-mi-foto-shell {
    --foto-tam: 216px;
    margin-inline: 0;
  }
}

.sobre-mi-foto__img {
  display: block;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  padding: 0;
  box-sizing: border-box;
}

@media (prefers-reduced-motion: reduce) {
  #sobre-mi .sobre-mi-foto-shell {
    opacity: 1;
    transform: none;
    transition: none;
  }

  .sobre-mi-foto-marco {
    animation: none;
    background: linear-gradient(
      145deg,
      rgba(var(--vin-acento-rgb), 0.55),
      rgba(255, 255, 255, 0.12)
    );
  }
}

/* Título de bloque: separación respecto al degradado / halo del fondo */
#sobre-mi > h3 {
  filter: drop-shadow(0 3px 18px rgba(8, 5, 9, 0.72));
}

#sobre-mi .sobre-mi-texto {
  flex: 0 1 auto;
  min-width: 0;
  max-width: min(100%, 40rem);
  text-align: justify;
  line-height: 1.65;
  font-size: clamp(0.88rem, 2.2vw, 0.98rem);
  font-weight: 500;
  color: #fdfdfd;
  text-shadow:
    0 1px 2px rgba(12, 8, 11, 0.92),
    0 2px 18px rgba(8, 5, 8, 0.65);
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