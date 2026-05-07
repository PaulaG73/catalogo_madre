<template>
    <div class="navBar">
      <nav id="navbar-principal" class="navbar navbar-dark bg-vin-negro border-bottom py-2 py-md-4 nav-vino">
        <div class="container-fluid nav-vino-layout">
          <div class="nav-logo-shell nav-logo-shell--round">
            <img
              class="nav-logo"
              src="/img/Logo Flores Eternamente Bellas (Imán circular) (1).png"
              alt="Logo Flores Eternamente Bellas"
              width="72"
              height="72"
              loading="lazy"
              decoding="async"
            >
          </div>
          <a class="navbar-brand d-flex align-items-center justify-content-center gap-2" href="#">
            <span class="navbar-brand-text">
              Celebremos a Mamá <span class="nav-title-break"><br></span>entre Copas y Flores
            </span>
          </a>
          <div class="nav-logo-shell nav-logo-shell--right">
            <img
              class="nav-logo"
              src="/img/logo-vinologa.png"
              alt="Logo Vinóloga"
              width="72"
              height="72"
              loading="lazy"
              decoding="async"
            >
          </div>
        </div>
      </nav>
    </div>
  </template>
  
  <script setup>
  
  
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
  .nav-vino {
    border-color: var(--vin-borde-sutil) !important;
    box-shadow: 0 1px 0 0 rgba(var(--vin-pastel-polvo-rgb), 0.45);
  }

  .nav-vino > .nav-vino-layout {
    --logo-size: clamp(56px, 8vw, 72px);
    display: grid;
    grid-template-columns: var(--logo-size) minmax(0, 1fr) var(--logo-size);
    align-items: center;
    width: 100%;
    gap: clamp(0.35rem, 1.5vw, 0.9rem);
    justify-content: initial;
    flex-wrap: nowrap;
  }

  .nav-logo-shell {
    inline-size: var(--logo-size);
    block-size: var(--logo-size);
    display: flex;
    align-items: center;
    justify-content: center;
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
    font-size: clamp(0.9rem, 2vw, 1.45rem);
    text-transform: uppercase;
    letter-spacing: clamp(0.015em, 0.18vw, 0.045em);
    line-height: 1.2;
    margin: 0;
    width: 100%;
    padding-inline: clamp(0.15rem, 0.8vw, 0.65rem);
    text-align: center;
    justify-content: center;
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

  .nav-title-break {
    display: none;
  }
  
  @media (min-width: 992px) {
    .nav-vino .navbar-brand {
      font-size: 1.5rem;
    }
  }
  
  @media (min-width: 1200px) {
    .nav-vino .navbar-brand {
      font-size: 1.68rem;
    }
  }

  @media (max-width: 991.98px) {
    .nav-vino > .nav-vino-layout {
      --logo-size: clamp(40px, 12vw, 56px);
      gap: 0.35rem;
    }

    .nav-vino .navbar-brand {
      justify-content: center !important;
      text-align: center;
      font-size: clamp(0.82rem, 3.3vw, 1.05rem);
      letter-spacing: 0.02em;
      line-height: 1.16;
      padding-inline: 0.15rem;
    }
  }

  @media (max-width: 575.98px) {
    .nav-vino > .nav-vino-layout {
      --logo-size: clamp(36px, 11vw, 44px);
      gap: 0.2rem;
    }

    .nav-vino .navbar-brand {
      font-size: clamp(0.72rem, 3.05vw, 0.9rem);
      letter-spacing: 0.01em;
    }

    .nav-title-break {
      display: inline;
    }
  }
  </style>
  