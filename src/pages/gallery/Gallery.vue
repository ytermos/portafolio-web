<script setup lang="ts">
import Autoplay from 'embla-carousel-autoplay'
import { Carousel, CarouselContent, CarouselItem } from '@/components/ui/carousel'
import { artworks, videos } from '@/pages/gallery-grid/data'

// Filtramos solo las de categoría "digital" y cogemos las 5 primeras para el carrusel
const digitalCarousel = artworks
  .filter((item) => item.category === 'digital')
  .slice(0, 5)

const autoplayDigital = Autoplay({
  delay: 4500,
  stopOnInteraction: false,
})

const traditionalCarousel = artworks
  .filter((item) => item.category === 'traditional')
  .slice(0, 5)

const designCarousel = artworks.filter((item) => item.category === 'design')

const autoplayTraditional = Autoplay({
  delay: 5200,
  stopOnInteraction: false,
})

const autoplayDesign = Autoplay({
  delay: 5800,
  stopOnInteraction: false,
})

const autoplayVideos = Autoplay({
  delay: 7000,
  stopOnInteraction: false,
})
</script>

<template>
    <div class="max-w-3xl mx-auto px-6 flex flex-col gap-24">
        
        <section>
            <h2 class="font-titulo text-lg tracking-[0.3em] text-stone-800 mb-4">
                DIGITAL ILLUSTRATION
            </h2>
            <Carousel :opts="{ loop: true, duration: 45 }" :plugins="[autoplayDigital]">
                <CarouselContent>
                <CarouselItem v-for="item in digitalCarousel" :key="item.id">
                    <img
                    :src="`/images/gallery/${item.category}/${item.image}`"
                    :alt="item.title"
                    class="w-full aspect-video object-cover"
                    />
                </CarouselItem>
                </CarouselContent>
            </Carousel>
        </section>

        
        <section>
            <h2 class="font-titulo text-lg tracking-[0.3em] text-stone-800 mb-4">
                TRADITIONAL ILLUSTRATION
            </h2>
            <Carousel :opts="{ loop: true, duration: 45 }" :plugins="[autoplayTraditional]">
                <CarouselContent>
                <CarouselItem v-for="item in traditionalCarousel" :key="item.id">
                    <img
                    :src="`/images/gallery/${item.category}/${item.image}`"
                    :alt="item.title"
                    class="w-full aspect-video object-cover"
                    />
                </CarouselItem>
                </CarouselContent>
            </Carousel>
        </section>

        
        <section>
            <h2 class="font-titulo text-lg tracking-[0.3em] text-stone-800 mb-4">
                DESIGN
            </h2>
            <Carousel :opts="{ loop: true, duration: 45 }" :plugins="[autoplayDesign]">
                <CarouselContent>
                <CarouselItem v-for="item in designCarousel" :key="item.id">
                    <img
                    :src="`/images/gallery/${item.category}/${item.image}`"
                    :alt="item.title"
                    class="w-full aspect-video object-cover"
                    />
                </CarouselItem>
                </CarouselContent>
            </Carousel>
        </section>
    

        <section>
            <h2 class="font-titulo text-lg tracking-[0.3em] text-stone-800 mb-4">
                VIDEOS
            </h2>
            <Carousel :opts="{ loop: true, duration: 45 }" :plugins="[autoplayVideos]">
                <CarouselContent>
                <CarouselItem v-for="item in videos" :key="item.id">
                    <video
                    :src="`/videos/${item.video}`"
                    autoplay
                    loop
                    muted
                    playsinline
                    class="w-full aspect-video object-cover"
                    />
                </CarouselItem>
                </CarouselContent>
            </Carousel>
        </section>
    </div>
</template>


<style scoped>

</style>