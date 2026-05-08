<template>
  <NavBar />

  <section id="sobre-mi" class="home-section home-section--ink pt-2 pb-3 py-md-4">
    <div class="container-fluid px-3 px-md-4 px-lg-5 sobre-mi-scroll-to-vinos text-start mb-2 mb-md-3">
      <a
        href="#packs"
        class="sobre-mi-scroll-to-vinos-link d-inline-flex align-items-center text-decoration-none"
        title="Ir al catálogo de vinos"
      >
        <span class="btn-top btn-top--rosa-circle flex-shrink-0" aria-hidden="true">
          <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor" viewBox="0 0 16 16" aria-hidden="true">
            <path fill-rule="evenodd" d="M8 4a.5.5 0 0 1 .5.5v5.793l2.146-2.147a.5.5 0 0 1 .708.708l-3 3a.5.5 0 0 1-.708 0l-3-3a.5.5 0 1 1 .708-.708L7.5 10.293V4.5A.5.5 0 0 1 8 4z"/>
          </svg>
        </span>
        <span class="sobre-mi-scroll-to-vinos-text">Ir al catálogo de vinos</span>
      </a>
    </div>
    <div class="container-fluid px-3 px-md-4 px-lg-5 sobre-mi sobre-mi--poema-flores py-3 py-md-4">
      <div class="row sobre-mi-poema-row align-items-center justify-content-center gx-2 gx-md-3 gx-xl-4 gy-4">
        <aside class="col-lg-3 d-none d-lg-flex sobre-mi-flores-col sobre-mi-flores-col--izq flex-column align-items-center">
          <div class="sobre-mi-flores-stack">
            <figure
              v-for="flor in sobreMiFloresIzq"
              :key="flor.src"
              class="sobre-mi-flor-figure mb-0"
            >
              <button
                type="button"
                class="sobre-mi-flor-trigger"
                :aria-label="`Ver detalle de ${flor.nombre}`"
                @click="openFlorModal(flor)"
              >
                <img
                  class="sobre-mi-flor-img"
                  :src="flor.src"
                  :alt="flor.nombre"
                  loading="lazy"
                  decoding="async"
                >
              </button>
            </figure>
          </div>
        </aside>
        <div class="col-12 col-lg-6 sobre-mi-poema-col">
          <div class="sobre-mi-texto sobre-mi-texto--poema-centro mx-auto">
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
        <div
          class="col-12 d-lg-none sobre-mi-flores-grid-movil"
          role="group"
          aria-label="Flores del catálogo"
        >
          <figure
            v-for="flor in sobreMiFloresGridMovil"
            :key="'grid-' + flor.src"
            class="sobre-mi-flor-figure mb-0"
          >
            <button
              type="button"
              class="sobre-mi-flor-trigger"
              :aria-label="`Ver detalle de ${flor.nombre}`"
              @click="openFlorModal(flor)"
            >
              <img
                class="sobre-mi-flor-img"
                :src="flor.src"
                :alt="flor.nombre"
                loading="lazy"
                decoding="async"
              >
            </button>
          </figure>
        </div>
        <aside class="col-lg-3 d-none d-lg-flex sobre-mi-flores-col sobre-mi-flores-col--der flex-column align-items-center">
          <div class="sobre-mi-flores-stack">
            <figure
              v-for="flor in sobreMiFloresDer"
              :key="flor.src"
              class="sobre-mi-flor-figure mb-0"
            >
              <button
                type="button"
                class="sobre-mi-flor-trigger"
                :aria-label="`Ver detalle de ${flor.nombre}`"
                @click="openFlorModal(flor)"
              >
                <img
                  class="sobre-mi-flor-img"
                  :src="flor.src"
                  :alt="flor.nombre"
                  loading="lazy"
                  decoding="async"
                >
              </button>
            </figure>
          </div>
        </aside>
      </div>
    </div>
    <div
      v-if="florModal"
      class="sobre-mi-flor-modal-backdrop"
      role="presentation"
      @click.self="closeFlorModal"
    >
      <article
        class="sobre-mi-flor-modal"
        role="dialog"
        aria-modal="true"
        :aria-label="`Detalle de ${florModal.nombre}`"
      >
        <button
          type="button"
          class="sobre-mi-flor-modal-close"
          aria-label="Cerrar popup de la flor"
          @click="closeFlorModal"
        >
          ×
        </button>
        <img
          class="sobre-mi-flor-modal-img"
          :src="florModal.src"
          :alt="florModal.nombre"
          loading="lazy"
          decoding="async"
        >
        <h4 class="sobre-mi-flor-modal-title mb-1">{{ florModal.nombre }}</h4>
        <p class="sobre-mi-flor-modal-price mb-0">{{ florModal.precio }}</p>
      </article>
    </div>
    <div class="sobre-mi-cierre">
      <a
        class="sobre-mi-whatsapp text-decoration-none"
        :href="whatsappCatalogoUrl"
        target="_blank"
        rel="noopener noreferrer"
        :class="{ 'opacity-50': !whatsappCatalogoReady }"
        :aria-disabled="!whatsappCatalogoReady"
        aria-label="Solicita información sobre más opciones de flores y ramos aquí por WhatsApp"
      >
        <span class="sobre-mi-whatsapp-label">Solicita información sobre más opciones de flores y ramos aquí</span>
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
    <div class="container packs-scroll-to-flores text-end mt-2">
      <a
        href="#sobre-mi"
        class="packs-scroll-to-flores-link d-inline-flex align-items-center text-decoration-none"
        title="Volver a las flores"
      >
        <span class="packs-scroll-to-flores-text">Volver a las flores</span>
        <span class="btn-top btn-top--rosa-circle flex-shrink-0" aria-hidden="true">
          <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" fill="currentColor" viewBox="0 0 16 16" aria-hidden="true">
            <path d="M8 12a.5.5 0 0 0 .5-.5V5.707l2.146 2.147a.5.5 0 0 0 .708-.708l-3-3a.5.5 0 0 0-.708 0l-3 3a.5.5 0 0 0 .708.708L7.5 5.707V11.5a.5.5 0 0 0 .5.5z"/>
          </svg>
        </span>
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

/** Flores laterales en «Sobre mí»: izquierda y derecha del poema */
const sobreMiFloresIzq = [
  { src: '/img/dalia.jpg', nombre: 'Dahlia', precio: '$8.000' },
  { src: '/img/orquídea.JPG', nombre: 'Orquídea con maceta', precio: '$20.000' },
  { src: '/img/gerbera.JPG', nombre: 'Gerbera', precio: '$8.000' },
]

const sobreMiFloresDer = [
  { src: '/img/tulipanes.JPG', nombre: 'Ramo de Tulipanes', precio: '$30.000' },
  { src: '/img/ramo_lilium.JPG', nombre: 'Ramo de Lirios', precio: '$40.000' },
  { src: '/img/ramo_mixto_3.JPG', nombre: 'Ramo mixto', precio: '$45.000' },
]

/** Por debajo del breakpoint lg: las 6 flores en rejilla 2×3 (columna izquierda y luego derecha del escritorio) */
const sobreMiFloresGridMovil = computed(() => [...sobreMiFloresIzq, ...sobreMiFloresDer])
const florModal = ref(null)

function openFlorModal(flor) {
  florModal.value = flor
}

function closeFlorModal() {
  florModal.value = null
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

#sobre-mi .sobre-mi-scroll-to-vinos-link {
  gap: clamp(0.45rem, 2vw, 0.85rem);
  color: #fff8fb;
  font-weight: 600;
  font-size: clamp(0.96rem, 2.4vw, 1.12rem);
  letter-spacing: 0.01em;
  text-shadow:
    0 1px 2px rgba(12, 8, 11, 0.92),
    0 0 18px rgba(8, 5, 8, 0.35);
}

#sobre-mi .sobre-mi-scroll-to-vinos {
  display: flex;
  justify-content: flex-start;
}

#packs .packs-scroll-to-flores-link {
  gap: clamp(0.45rem, 2vw, 0.85rem);
  color: #fff8fb;
  font-weight: 600;
  font-size: clamp(0.96rem, 2.4vw, 1.12rem);
  letter-spacing: 0.01em;
  text-shadow:
    0 1px 2px rgba(12, 8, 11, 0.92),
    0 0 18px rgba(8, 5, 8, 0.35);
}

#packs .packs-scroll-to-flores {
  display: flex;
  justify-content: flex-end;
}

#packs .packs-scroll-to-flores-link:hover {
  color: #ffeef8;
}

#packs .packs-scroll-to-flores-link:hover .packs-scroll-to-flores-text,
#packs .packs-scroll-to-flores-link:focus-visible .packs-scroll-to-flores-text {
  text-decoration: underline;
  text-underline-offset: 0.15em;
}

#packs .packs-scroll-to-flores-link:focus-visible {
  outline: 2px solid rgba(var(--vin-rosa-sorbete-rgb), 0.6);
  outline-offset: 4px;
  border-radius: 0.35rem;
}

#sobre-mi .sobre-mi-scroll-to-vinos-link:hover {
  color: #ffeef8;
}

#sobre-mi .sobre-mi-scroll-to-vinos-link:hover .sobre-mi-scroll-to-vinos-text,
#sobre-mi .sobre-mi-scroll-to-vinos-link:focus-visible .sobre-mi-scroll-to-vinos-text {
  text-decoration: underline;
  text-underline-offset: 0.15em;
}

#sobre-mi .sobre-mi-scroll-to-vinos-link:focus-visible {
  outline: 2px solid rgba(var(--vin-rosa-sorbete-rgb), 0.6);
  outline-offset: 4px;
  border-radius: 0.35rem;
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

/* Poema central + columnas de fotos (izq / der) */
#sobre-mi .sobre-mi--poema-flores {
  padding-block: clamp(0.75rem, 3vw, 1.75rem);
}

#sobre-mi .sobre-mi-texto--poema-centro {
  text-align: center;
  max-width: min(100%, 34rem);
}

@media (max-width: 991.98px) {
  #sobre-mi .sobre-mi-texto--poema-centro {
    font-size: clamp(1.02rem, 3.5vw, 1.22rem);
    line-height: 1.72;
  }
}

@media (max-width: 575.98px) {
  #sobre-mi .sobre-mi-texto--poema-centro {
    font-size: clamp(1.08rem, 4.4vw, 1.28rem);
    line-height: 1.76;
  }
}

@media (min-width: 768px) and (max-width: 991.98px) {
  #sobre-mi .sobre-mi-cierre {
    font-size: clamp(1.02rem, 3.5vw, 1.22rem);
  }
}

@media (min-width: 992px) {
  #sobre-mi .sobre-mi-cierre {
    font-size: clamp(0.96rem, 2vw, 1.16rem);
  }
}

#sobre-mi .sobre-mi-flores-stack {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: clamp(0.4rem, 1.35vw, 0.75rem);
}

#sobre-mi .sobre-mi-flor-figure {
  width: 100%;
  max-width: min(100%, clamp(84px, 18vw, 128px));
}

#sobre-mi .sobre-mi-flor-trigger {
  display: block;
  width: 100%;
  padding: 0;
  margin: 0;
  border: none;
  border-radius: 0.62rem;
  background: transparent;
  cursor: pointer;
}

#sobre-mi .sobre-mi-flor-trigger:focus-visible {
  outline: 2px solid rgba(var(--vin-rosa-sorbete-rgb), 0.68);
  outline-offset: 3px;
}

@media (min-width: 768px) and (max-width: 991.98px) {
  #sobre-mi .sobre-mi-flor-figure {
    max-width: min(100%, clamp(88px, 14vw, 118px));
  }
}

@media (min-width: 992px) {
  #sobre-mi .sobre-mi-flores-col .sobre-mi-flor-figure {
    max-width: min(100%, clamp(96px, 11vw, 132px));
  }
}

/* Por debajo de lg: las 6 fotos en 2 filas × 3 columnas (tras el poema) */
@media (max-width: 991.98px) {
  #sobre-mi .sobre-mi-flores-grid-movil {
    display: grid;
    grid-template-columns: repeat(3, minmax(0, 1fr));
    column-gap: clamp(0.22rem, 1.75vw, 0.42rem);
    row-gap: clamp(0.32rem, 2.2vw, 0.52rem);
    width: 100%;
    max-width: min(100%, 18.25rem);
    margin-inline: auto;
    padding-inline: 0.12rem;
  }

  #sobre-mi .sobre-mi-flores-grid-movil .sobre-mi-flor-figure {
    max-width: none;
    width: 100%;
  }
}

#sobre-mi .sobre-mi-flor-img {
  display: block;
  width: 100%;
  aspect-ratio: 4 / 5;
  object-fit: cover;
  border-radius: 0.62rem;
  border: 2px solid rgba(255, 214, 232, 0.38);
  box-shadow:
    0 6px 18px rgba(8, 5, 9, 0.38),
    0 0 0 1px rgba(255, 236, 245, 0.14);
  transition:
    transform 0.22s ease,
    box-shadow 0.22s ease,
    border-color 0.22s ease;
}

#sobre-mi .sobre-mi-flor-modal-backdrop {
  position: fixed;
  inset: 0;
  z-index: 1080;
  background: rgba(15, 10, 14, 0.72);
  backdrop-filter: blur(2px);
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 1rem;
}

#sobre-mi .sobre-mi-flor-modal {
  position: relative;
  width: min(100%, 22rem);
  border-radius: 1rem;
  background: linear-gradient(165deg, #3d3340 0%, #2f2833 100%);
  border: 1px solid rgba(255, 214, 232, 0.35);
  box-shadow: 0 20px 44px rgba(4, 2, 4, 0.5);
  padding: 1rem 1rem 1.1rem;
  text-align: center;
}

#sobre-mi .sobre-mi-flor-modal-close {
  position: absolute;
  top: 0.45rem;
  right: 0.45rem;
  width: 2rem;
  height: 2rem;
  border: none;
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.14);
  color: #fff;
  font-size: 1.22rem;
  line-height: 1;
  cursor: pointer;
}

#sobre-mi .sobre-mi-flor-modal-close:hover {
  background: rgba(255, 255, 255, 0.24);
}

#sobre-mi .sobre-mi-flor-modal-close:focus-visible {
  outline: 2px solid rgba(var(--vin-rosa-sorbete-rgb), 0.75);
  outline-offset: 2px;
}

#sobre-mi .sobre-mi-flor-modal-img {
  display: block;
  width: min(100%, 13.5rem);
  aspect-ratio: 4 / 5;
  object-fit: cover;
  border-radius: 0.72rem;
  margin: 0.2rem auto 0.8rem;
  border: 2px solid rgba(255, 214, 232, 0.45);
  box-shadow: 0 10px 22px rgba(7, 4, 8, 0.42);
}

#sobre-mi .sobre-mi-flor-modal-title {
  color: #ffe8f2;
  font-size: clamp(1.05rem, 3.4vw, 1.28rem);
  font-weight: 800;
  letter-spacing: 0.01em;
}

#sobre-mi .sobre-mi-flor-modal-price {
  color: #ffd6e8;
  font-size: clamp(0.98rem, 3vw, 1.12rem);
  font-weight: 700;
}

@media (hover: hover) and (pointer: fine) {
  #sobre-mi .sobre-mi-flor-img:hover {
    transform: scale(1.035);
    border-color: rgba(255, 236, 245, 0.58);
    box-shadow:
      0 12px 26px rgba(8, 5, 9, 0.44),
      0 0 0 2px rgba(var(--vin-rosa-sorbete-rgb), 0.28);
  }
}

@media (prefers-reduced-motion: reduce) {
  #sobre-mi .sobre-mi-flor-img {
    transition: border-color 0.15s ease, box-shadow 0.15s ease;
  }

  @media (hover: hover) and (pointer: fine) {
    #sobre-mi .sobre-mi-flor-img:hover {
      transform: none;
    }
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