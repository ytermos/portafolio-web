<script setup lang="ts">
import { ref } from 'vue';
import { Circle, Minus } from 'lucide-vue-next';



interface MenuItems {
  label: string;
  href: string;
  onClick?: () => void;
}

defineProps<{
  items: MenuItems[]
}>();

const isOpen = ref(false);


const toggleMenu = () => {
  isOpen.value = !isOpen.value};

const handleNavigate = (href: string, customClick?: () => void) => {
  if (customClick) {
    customClick();
  }
  isOpen.value = false;

  const target = document.querySelector(href);
  if (target) {
    target.scrollIntoView({ behavior: 'smooth' });
  }
};



</script>

<template>
  
  <div
    v-if="isOpen"
    @click="isOpen = false"
    class="fixed inset-0 z-40"
  ></div>

  
  <div class=" nav-shadow fixed top-4 left-4 right-4 z-50 flex flex-col sm:flex-row sm:items-center pointer-events-none text-white">
    
    
    <button
  type="button"
  class="mt-5 ml-5 w-20 h-20 rounded-full flex items-center justify-center p-0 bg-transparent cursor-pointer pointer-events-auto focus:outline-none transition-all duration-300 hover:scale-105 hover:text-orange-100"
  @click="toggleMenu"
>
  <Transition name="icon-switch" mode="out-in">
    <Circle v-if="!isOpen" class="size-full" />
    <span v-else class="size-full inline-flex items-center justify-center">
      <Minus class="size-full sm:rotate-90 transition-transform duration-300" />
    </span>
  </Transition>
</button>

    
    <Transition name="slide-menu" :duration="{ enter: 1500, leave: 400 }">
      <nav 
        v-if="isOpen"
        class="relative flex flex-col sm:flex-row  w-fit sm:ml-auto sm:pl-40 mt-2 sm:mt-0 pointer-events-auto"
      >
        <a
          v-for="item in items"
          :key="item.label"
          :href="item.href"
          @click.prevent="handleNavigate(item.href, item.onClick)"
          class="px-4 py-3 hover:text-orange-100 transition-colors duration-300"
        >
          {{ item.label }}
        </a>
        <span class="menu-line absolute bg-white top-0 right-0 w-[3px] h-full sm:top-auto sm:bottom-0 sm:left-0 sm:w-full sm:h-[3px] "></span>

      </nav>
    </Transition>

  </div>
</template>


<style scoped>
.nav-shadow {
  filter: drop-shadow(0 2px 6px rgba(0, 0, 0, 0.45));
}

.slide-menu-enter-active,
.slide-menu-leave-active {
  transition: transform 0.4s ease, opacity 0.4s ease;
}


.slide-menu-enter-from,
.slide-menu-leave-to {
  opacity: 0;
  transform: translateY(-20px);
}


@media (min-width: 640px) {
  .slide-menu-enter-from,
  .slide-menu-leave-to {
    opacity: 0;
    transform: translateX(-40px);
  }
}


.slide-menu-enter-active a {
  transition: transform 0.6s ease, opacity 0.6s ease;
}


.slide-menu-enter-from a {
  opacity: 0;
  transform: translateY(-60px);
}

@media (min-width: 640px) {
  .slide-menu-enter-from a {
    transform: translateX(-24rem);
  }
}


.slide-menu-enter-active a:nth-child(1) { transition-delay: 0.55s; }
.slide-menu-enter-active a:nth-child(2) { transition-delay: 0.30s; }
.slide-menu-enter-active a:nth-child(3) { transition-delay: 0.05s; }


.icon-switch-enter-active,
.icon-switch-leave-active {
  transition: opacity 0.25s ease;
}

.icon-switch-enter-from,
.icon-switch-leave-to {
  opacity: 0;
}


.slide-menu-enter-active .menu-line {
  transition: transform 0.5s ease-out;
  transition-delay: 0.75s;
}

.slide-menu-enter-from .menu-line {
  transform: scaleY(0);
}

@media (min-width: 640px) {
  .slide-menu-enter-from .menu-line {
    transform: scaleX(0);
  }
}

</style>