<script setup lang="ts">
import Autoplay from 'embla-carousel-autoplay'
import { Carousel,
  CarouselContent,
  CarouselItem,
  CarouselNext,
  CarouselPrevious,} from '@/components/ui/carousel'
import { artworks, videos } from '@/pages/gallery-grid/data'
import { ChevronLeft, ChevronRight } from 'lucide-vue-next'

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
    <div class="max-w-4xl mx-auto px-14 sm:px-20 pb-24 flex flex-col gap-60">
        
        <section class="w-full flex flex-col items-center">
            <Carousel :opts="{ loop: true, duration: 45 }" :plugins="[autoplayDigital]" class="w-full">
                
                <CarouselContent>
                    <CarouselItem v-for="item in digitalCarousel" :key="item.id">
                        <div class="h-[340px] sm:h-[460px] md:h-[540px] flex items-center justify-center cursor-pointer">
                            <img
                            :src="`/images/gallery/${item.category}/${item.image}`"
                            :alt="item.title"
                            class="max-h-full max-w-full object-contain"
                            />
                        </div>
                    </CarouselItem>
                </CarouselContent>
                    <CarouselPrevious class="border-none bg-transparent shadow-none text-stone-300 hover:text-stone-100 hover:bg-transparent cursor-pointer">
                        <ChevronLeft class="size-7" :stroke-width="1.75" />
                    </CarouselPrevious>
                    <CarouselNext class="border-none bg-transparent shadow-none text-stone-300 hover:text-stone-100 hover:bg-transparent cursor-pointer">
                        <ChevronRight class="size-7" :stroke-width="1.75" />
                    </CarouselNext>
               </Carousel>
               <div class="mt-6 flex flex-col items-center text-center">
                    <h2 class="font-titulo text-lg sm:text-xl tracking-[0.4em] pl-[0.3em] text-stone-200">
                    DIGITAL ILLUSTRATION
                    </h2>
                    
                    <button
                    type="button"
                    class="mt-2 text-xs tracking-[0.25em] pl-[0.25em] text-stone-400 hover:text-stone-100 transition-colors cursor-pointer"
                    >
                    Go to gallery
                    </button>
                </div>
            
        </section>

        
        <section class="w-full flex flex-col items-center">
            <Carousel :opts="{ loop: true, duration: 45 }" :plugins="[autoplayTraditional]" class="w-full">
                <CarouselContent>
                <CarouselItem v-for="item in traditionalCarousel" :key="item.id">
                    <div class="h-[340px] sm:h-[460px] md:h-[540px] flex items-center justify-center cursor-pointer"> 
                        <img
                        :src="`/images/gallery/${item.category}/${item.image}`"
                        :alt="item.title"
                        class="max-h-full max-w-full object-contain"
                        />
                    </div>
                </CarouselItem>
                </CarouselContent>
                    <CarouselPrevious class="border-none bg-transparent shadow-none text-stone-300 hover:text-stone-100 hover:bg-transparent cursor-pointer">
                        <ChevronLeft class="size-7" :stroke-width="1.75" />
                    </CarouselPrevious>
                    <CarouselNext class="border-none bg-transparent shadow-none text-stone-300 hover:text-stone-100 hover:bg-transparent cursor-pointer">
                        <ChevronRight class="size-7" :stroke-width="1.75" />
                    </CarouselNext>
            </Carousel>
            <div class="mt-6 flex flex-col items-center text-center">
                <h2 class="font-titulo text-lg sm:text-xl tracking-[0.4em] pl-[0.3em] text-stone-200">
                TRADITIONAL ILLUSTRATION
                </h2>
                <button
                type="button"
                class="mt-2 text-xs tracking-[0.25em] pl-[0.25em] text-stone-400 hover:text-stone-100 transition-colors cursor-pointer"
                >
                Go to gallery
                </button>
            </div>
        </section>

        
        <section class="w-full flex flex-col items-center">
            <Carousel :opts="{ loop: true, duration: 45 }" :plugins="[autoplayDesign]" class="w-full">
                <CarouselContent>
                    <CarouselItem v-for="item in designCarousel" :key="item.id">
                        <div class="h-[340px] sm:h-[460px] md:h-[540px] flex items-center justify-center cursor-pointer">
                            <img
                            :src="`/images/gallery/${item.category}/${item.image}`"
                            :alt="item.title"
                            class="max-h-full max-w-full object-contain"
                            />
                        </div>
                    </CarouselItem>
                </CarouselContent>
                    <CarouselPrevious class="border-none bg-transparent shadow-none text-stone-300 hover:text-stone-100 hover:bg-transparent cursor-pointer">
                        <ChevronLeft class="size-7" :stroke-width="1.75" />
                    </CarouselPrevious>
                    <CarouselNext class="border-none bg-transparent shadow-none text-stone-300 hover:text-stone-100 hover:bg-transparent cursor-pointer">
                        <ChevronRight class="size-7" :stroke-width="1.75" />
                    </CarouselNext>
            </Carousel>
            <div class="mt-6 flex flex-col items-center text-center">
                <h2 class="font-titulo text-lg sm:text-xl tracking-[0.4em] pl-[0.3em] text-stone-200">
                DESIGN
                </h2>
                <button
                type="button"
                class="mt-2 text-xs tracking-[0.25em] pl-[0.25em] text-stone-400 hover:text-stone-100 transition-colors cursor-pointer"
                >
                Go to gallery
                </button>
            </div>
        </section>
    

        <section class="w-full flex flex-col items-center ">
            <Carousel :opts="{ loop: true, duration: 45 }" :plugins="[autoplayVideos]" class="w-full">
                <CarouselContent>
                    <CarouselItem v-for="item in videos" :key="item.id">
                        <div class="h-[340px] sm:h-[460px] md:h-[540px] flex items-center justify-center cursor-pointer">
                            <video
                            :src="`/videos/${item.video}`"
                            autoplay
                            loop
                            muted
                            playsinline
                            class="max-h-full max-w-full object-contain pointer-events-none"
                            />
                        </div>
                    </CarouselItem>
                </CarouselContent>
                    <CarouselPrevious class="border-none bg-transparent shadow-none text-stone-300 hover:text-stone-100 hover:bg-transparent cursor-pointer">
                        <ChevronLeft class="size-7" :stroke-width="1.75" />
                    </CarouselPrevious>
                    <CarouselNext class="border-none bg-transparent shadow-none text-stone-300 hover:text-stone-100 hover:bg-transparent cursor-pointer">
                        <ChevronRight class="size-7" :stroke-width="1.75" />
                    </CarouselNext>
            </Carousel>
            <div class="mt-6 flex flex-col items-center text-center">
                <h2 class="font-titulo text-lg sm:text-xl tracking-[0.4em] pl-[0.3em] text-stone-200">
                VIDEOS
                </h2>
                <button
                type="button"
                class="mt-2 text-xs tracking-[0.25em] pl-[0.25em] text-stone-400 hover:text-stone-100 transition-colors cursor-pointer"
                >
                Go to gallery
                </button>
            </div>
        </section>
    </div>
</template>


<style scoped>

</style>