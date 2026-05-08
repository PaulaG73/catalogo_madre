<template>
    <div class="navBar">
      <nav id="navbar-principal" class="navbar navbar-dark bg-vin-negro border-bottom nav-vino">
        <div class="container-fluid nav-vino-layout">
          <div class="nav-logo-shell nav-logo-shell--round">
            <img
              class="nav-logo"
              src="/img/Logo Flores Eternamente Bellas (Imán circular) (1).png"
              alt="Logo Flores Eternamente Bellas"
              width="84"
              height="84"
              loading="lazy"
              decoding="async"
            >
          </div>
          <a class="navbar-brand d-flex flex-column align-items-center justify-content-center" href="#">
            <span class="navbar-brand-text navbar-brand-text--main">
              Celebremos a Mamá <span class="nav-title-break"><br></span>entre Copas y Flores
            </span>
            <span class="navbar-brand-subtitle">Vinóloga ft Flores eternamente bellas</span>
          </a>
          <div class="nav-logo-shell nav-logo-shell--right">
            <img
              class="nav-logo"
              src="/img/logo-vinologa.png"
              alt="Logo Vinóloga"
              width="84"
              height="84"
              loading="lazy"
              decoding="async"
            >
          </div>
          <p class="navbar-brand-note mb-0">
            Agrega una hermosa flor o ramo de "Flores eternamente bellas" a tu botella de vino o espumante y dale un sello especial a tu regalo.
          </p>
        </div>
      </nav>
    </div>
  </template>
  
  <script setup>
  
  
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
  .nav-vino {
    padding-block: clamp(0.7rem, 1.9vw, 1.25rem);
    border-color: var(--vin-borde-sutil) !important;
    box-shadow: 0 1px 0 0 rgba(var(--vin-pastel-polvo-rgb), 0.45);
  }

  .nav-vino > .nav-vino-layout {
    --logo-size: clamp(78px, 10.8vw, 108px);
    display: grid;
    grid-template-columns: minmax(var(--logo-size), var(--logo-size)) minmax(0, 1fr) minmax(var(--logo-size), var(--logo-size));
    grid-template-areas:
      "logo-left brand logo-right"
      "logo-left note logo-right";
    align-items: center;
    width: 100%;
    gap: clamp(0.35rem, 1.5vw, 0.9rem);
    justify-content: initial;
    flex-wrap: nowrap;
  }

  .nav-logo-shell--round {
    grid-area: logo-left;
  }

  .nav-vino .navbar-brand {
    grid-area: brand;
  }

  .nav-logo-shell--right {
    grid-area: logo-right;
  }

  .nav-logo-shell {
    inline-size: var(--logo-size);
    block-size: var(--logo-size);
    display: flex;
    align-items: center;
    justify-content: center;
    align-self: center;
  }

  .nav-logo-shell--round {
    border-radius: 50%;
    overflow: hidden;
  }

  .nav-logo {
    inline-size: 100%;
    block-size: 100%;
    object-fit: contain;
    object-position: center;
    display: block;
  }

  .nav-vino .navbar-brand,
  .nav-vino .nav-link {
    font-family: 'Nunito', system-ui, sans-serif;
    color: rgba(255, 255, 255, 0.92);
  }
  
  .nav-vino .navbar-brand:hover .navbar-brand-text,
  .nav-vino .navbar-brand:focus-visible .navbar-brand-text {
    color: #ffe8f2;
  }

  .nav-vino .navbar-brand:focus-visible {
    outline: 2px solid rgba(var(--vin-rosa-sorbete-rgb), 0.55);
    outline-offset: 4px;
    border-radius: 0.35rem;
  }
  
  /* Hover / foco solo en enlaces del menú (Vinos y espumantes, Contacto) */
  .nav-vino .navbar-nav .nav-link {
    position: relative;
    padding-inline: 0.75rem;
    padding-block: 0.4rem;
    border-radius: 0.4rem;
    transition:
      color 0.2s ease,
      background-color 0.2s ease,
      transform 0.2s ease;
  }
  
  .nav-vino .navbar-nav .nav-link::after {
    content: '';
    position: absolute;
    left: 50%;
    bottom: 0.15rem;
    width: 0;
    height: 2px;
    border-radius: 2px;
    background: linear-gradient(
      90deg,
      rgba(var(--vin-pastel-polvo-rgb), 0.95),
      rgba(var(--vin-pastel-nube-rgb), 0.98)
    );
    transform: translateX(-50%);
    transition: width 0.28s ease;
  }
  
  .nav-vino .navbar-nav .nav-link:hover,
  .nav-vino .navbar-nav .nav-link:focus-visible {
    color: #fff;
    background-color: rgba(255, 255, 255, 0.1);
    transform: translateY(-2px);
  }
  
  .nav-vino .navbar-nav .nav-link:hover::after,
  .nav-vino .navbar-nav .nav-link:focus-visible::after {
    width: calc(100% - 1.1rem);
  }
  
  @media (prefers-reduced-motion: reduce) {
    .nav-vino .navbar-nav .nav-link {
      transition: color 0.15s ease, background-color 0.15s ease;
    }
  
    .nav-vino .navbar-nav .nav-link:hover,
    .nav-vino .navbar-nav .nav-link:focus-visible {
      transform: none;
    }
  
    .nav-vino .navbar-nav .nav-link::after {
      transition: width 0.15s ease;
    }
  }
  
  .nav-vino .navbar-brand {
    font-size: clamp(1.05rem, 2.4vw, 1.75rem);
    text-transform: uppercase;
    letter-spacing: clamp(0.015em, 0.18vw, 0.045em);
    line-height: 1.2;
    margin: 0;
    width: 100%;
    max-width: 100%;
    min-width: 0;
    padding-inline: clamp(0.15rem, 0.8vw, 0.65rem);
    text-align: center;
    justify-content: center;
    justify-self: center;
    overflow: hidden;
  }

  /* Misma lectura que #sobre-mi .sobre-mi-vino-mayus */
  .nav-vino .navbar-brand-text {
    color: #ffd6e8;
    font-weight: 800;
    display: block;
    white-space: normal;
    word-break: break-word;
    overflow-wrap: anywhere;
    text-shadow:
      0 1px 3px rgba(14, 10, 12, 0.98),
      0 2px 4px rgba(8, 5, 9, 0.92),
      0 0 22px rgba(var(--vin-rosa-sorbete-rgb), 0.42),
      0 0 3px rgba(58, 15, 24, 0.85);
  }

  .nav-vino .navbar-brand-subtitle {
    display: block;
    margin-top: 0.28rem;
    font-family: "Palatino Linotype", "Book Antiqua", Palatino, Georgia, serif;
    font-style: italic;
    font-weight: 600;
    font-size: clamp(0.76rem, 1.45vw, 1.02rem);
    line-height: 1.18;
    letter-spacing: 0.012em;
    text-transform: none;
    white-space: normal;
    color: rgba(255, 236, 245, 0.98);
    text-shadow: 0 1px 3px rgba(8, 5, 9, 0.85);
  }

  .nav-vino .navbar-brand-note {
    grid-area: note;
    display: block;
    margin-top: clamp(0.15rem, 0.7vw, 0.35rem);
    font-family: 'Nunito', system-ui, sans-serif;
    font-style: normal;
    font-weight: 600;
    font-size: clamp(0.68rem, 1.35vw, 0.84rem);
    line-height: 1.35;
    letter-spacing: 0.005em;
    text-transform: none;
    color: rgba(255, 242, 248, 0.94);
    text-shadow: 0 1px 2px rgba(8, 5, 9, 0.78);
    width: 100%;
    max-width: min(100%, 68ch);
    margin-inline: auto;
    text-align: center;
    padding-inline: clamp(0.35rem, 1.5vw, 1.2rem);
    overflow-wrap: anywhere;
  }

  .nav-title-break {
    display: none;
  }
  
  @media (min-width: 992px) {
    .nav-vino .navbar-brand {
      font-size: 1.72rem;
    }
  }
  
  @media (min-width: 1200px) {
    .nav-vino .navbar-brand {
      font-size: 1.95rem;
    }
  }

  @media (max-width: 991.98px) {
    .nav-vino {
      padding-block: clamp(0.6rem, 2.4vw, 0.95rem);
    }

    .nav-vino > .nav-vino-layout {
      --logo-size: clamp(60px, 13vw, 82px);
      gap: 0.35rem;
      grid-template-areas:
        "logo-left brand logo-right"
        "logo-left note logo-right";
    }

    .nav-vino .navbar-brand {
      justify-content: center !important;
      text-align: center;
      font-size: clamp(1rem, 3.6vw, 1.3rem);
      letter-spacing: 0.02em;
      line-height: 1.16;
      padding-inline: 0.15rem;
    }

    .nav-vino .navbar-brand-subtitle {
      font-size: clamp(0.72rem, 2.4vw, 0.92rem);
    }

    .nav-vino .navbar-brand-note {
      font-size: clamp(0.64rem, 2.05vw, 0.77rem);
      line-height: 1.3;
      margin-top: 0.24rem;
      max-width: min(100%, 62ch);
      padding-inline: 0.3rem;
    }
  }

  @media (max-width: 575.98px) {
    .nav-vino > .nav-vino-layout {
      --logo-size: clamp(48px, 12vw, 64px);
      gap: 0.2rem;
      grid-template-columns: var(--logo-size) minmax(0, 1fr) var(--logo-size);
      grid-template-areas:
        "logo-left brand logo-right"
        "logo-left note logo-right";
    }

    .nav-vino .navbar-brand {
      font-size: clamp(0.95rem, 4.4vw, 1.24rem);
      letter-spacing: 0.01em;
      line-height: 1.12;
    }

    .nav-vino .navbar-brand-text {
      overflow-wrap: break-word;
      word-break: normal;
    }

    .nav-vino .navbar-brand-subtitle {
      font-size: clamp(0.7rem, 3vw, 0.9rem);
      white-space: normal;
      overflow-wrap: anywhere;
      line-height: 1.2;
      margin-top: 0.2rem;
    }

    .nav-vino .navbar-brand-note {
      font-size: clamp(0.62rem, 2.75vw, 0.74rem);
      line-height: 1.25;
      letter-spacing: 0;
      margin-top: 0.18rem;
      max-width: min(100%, 52ch);
      padding-inline: 0.2rem;
    }

    .nav-title-break {
      display: inline;
    }
  }
  </style>
  