<script setup lang="ts">
import NavBar from '@/components/NavBar.vue';
import Gallery from '../gallery/Gallery.vue';
import About from '../about/About.vue';


// import { Button } from '@/components/ui/button'

const menuItems = [
  { label: 'Home', href: '#home' },
  { label: 'Gallery', href: '#gallery' },
  { label: 'About', href: '#about' },
];

</script>

<template>
  <div >
    <div class="velo-blanco fixed inset-0 z-40 bg-pink-800/15 pointer-events-none"></div>
      <header class="entrada-navbar relative z-50">
        <NavBar :items="menuItems" />
      </header>

      <section id="home" class="relative min-h-screen">
        <div class="fondo-portada absolute top-0 inset-x-0 pointer-events-none">
          <img
            src="/images/homeimages/fondo-portada.jpg"
            alt=""
            class="w-full h-full object-cover object-center"
          />
          
        </div>

        <div class="relative z-10 min-h-screen flex flex-col items-center px-6"> 

          <div class="relative flex-1 w-full flex justify-center mb-8 sm:mb-10 pointer-events-none">
            <div class="linea-top absolute top-[50%] sm:top-[50%] bottom-0 w-[3px]"></div>
          </div>

            <div class="flex flex-col items-center text-center">
              <p class="entrada-1 mb-4 sm:mb-6 text-xs sm:text-sm tracking-[0.35em] pl-[0.35em] text-stone-900/80">
                PORTFOLIO · 2026
              </p>

              <h1 class="entrada-2 font-titulo font-extrabold text-center text-3xl sm:text-4xl md:text-5xl lg:text-6xl xl:text-7xl tracking-[0.40em] pl-[0.40em] text-stone-800 ">
                YAGO TERRER
              </h1>

              <p class="entrada-3 mt-4 sm:mt-6 font-semibold text-sm sm:text-base md:text-lg  tracking-[0.2em] pl-[0.2em] text-stone-900/80">
              ILLUSTRATION · 3D ANIMATION · MOTION GRAPHICS · GRAPHIC & WEB DESIGN
              </p>
            </div>

          <div class="relative flex-1 w-full flex justify-center mt-8 sm:mt-10 pointer-events-none"> 
          <div class="linea-bottom absolute top-0 -bottom-[180px] w-[3px]"></div>
          </div>
        </div>
      </section>

      <section id="gallery" class="min-h-screen pt-30">
        <div class=" relative z-10"> 
          <Gallery/>
        </div>
      </section>

      <section id="about" class="min-h-screen pt-30">
        <About/>
      </section>
  </div>
</template>

<style scoped>
.fondo-portada {

  height: calc(100% + 180px);
  -webkit-mask-image: linear-gradient(to bottom, black 65%, transparent 100%);
  mask-image: linear-gradient(to bottom, black 65%, transparent 100%);
  
}

.linea-top {
  background: linear-gradient(to bottom, transparent 0%, var(--color-stone-600, #292524) 45%);
  transform-origin: top;
  animation: line-fall 0.22s linear 0.2s both;
}

.linea-bottom {
  background: linear-gradient(to bottom, var(--color-stone-600, #292524) 0%, var(--background) 100%);
  transform-origin: top;
  animation: line-fall 1.15s cubic-bezier(0.3, 0.5, 0.25, 1) 0.62s both;
}

@keyframes line-fall {
  from {
    transform: scaleY(0);
  }
  to {
    transform: scaleY(1);
  }
}

.velo-blanco {
  animation: desvanecer-blanco 2s ease-out forwards;
}

.entrada-navbar {
  animation: bajar-navbar 1s ease-in-out 0.15s backwards;
}

.entrada-1,
.entrada-2,
.entrada-3 {
  animation: fade-down 0.7s cubic-bezier(0.22, 1, 0.36, 1) both;
}

.entrada-1 { animation-delay: 0.15s; }
.entrada-2 { animation-delay: 0.3s; }
.entrada-3 { animation-delay: 0.45s; }

@keyframes desvanecer-blanco {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}

@keyframes bajar-navbar {
  from {
    opacity: 0;
    transform: translateY(-25px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fade-down {
  from {
    opacity: 0;
    transform: translateY(-14px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>

<!-- <h1 class="text-3xl text-red-500 font-bold">
    Página Principal
  </h1>
 
  <Button>Botón de Shadcn</Button> -->
