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
  <div>
    <NavBar :items="menuItems" />
      <section id="home" class="min-h-screen pt-30 ">
        <h1>Portada</h1>
        <p>párrafo</p>
      </section>

      <section id="gallery" class="min-h-screen pt-30">
        <Gallery/>
      </section>

      <section id="about" class="min-h-screen pt-30">
        <About/>
      </section>
  </div>
</template>

<style scoped>

</style>

<!-- <h1 class="text-3xl text-red-500 font-bold">
    Página Principal
  </h1>
 
  <Button>Botón de Shadcn</Button> -->
