<script setup lang="ts">
import { ref } from 'vue';
import { Toggle } from '@/components/ui/toggle';
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

  
  <div class="fixed top-4 left-4 right-4 z-50 flex flex-col sm:flex-row sm:items-center">
    
    
    <Toggle 
  class="w-14 h-14 rounded-full flex items-center justify-center p-0 hover:bg-gray-100 transition-all duration-300"
  @click="toggleMenu"
>
  <Transition name="icon-switch" mode="out-in">
    <Circle v-if="!isOpen" class="size-full" />
    <span v-else class="size-full inline-flex items-center justify-center">
      <Minus class="size-full sm:rotate-90 transition-transform duration-300" />
    </span>
  </Transition>
</Toggle>

    
    <Transition name="slide-menu" :duration="{ enter: 1500, leave: 400 }">
      <nav 
        v-if="isOpen"
        class="relative flex flex-col sm:flex-row  w-fit sm:ml-auto sm:pl-40 mt-2 sm:mt-0 bg-white"
      >
        <a
          v-for="item in items"
          :key="item.label"
          :href="item.href"
          @click.prevent="handleNavigate(item.href, item.onClick)"
          class="px-4 py-3 hover:text-gray-500 transition-colors"
        >
          {{ item.label }}
        </a>
        <span class="menu-line absolute bg-gray-800 top-0 right-0 w-[3px] h-full sm:top-auto sm:bottom-0 sm:left-0 sm:w-full sm:h-[3px] "></span>

      </nav>
    </Transition>

  </div>
</template>


<style scoped>
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