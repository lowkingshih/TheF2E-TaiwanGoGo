<script>
  import Logo from "./Logo.vue";
  import NavBar from "./NavBar.vue";
  import { ref } from "vue";
  export default {
    components: {
      Logo,
      NavBar,
    },
    setup() {
      const isOpen = ref(false);
      const HandIsOpen = () => {
        isOpen.value = !isOpen.value;
      };
      const HandCloseOpen = () => {
        console.log(isOpen.value);
        if (isOpen.value) {
          isOpen.value = false;
        }
      };
      return {
        isOpen,
        HandIsOpen,
        HandCloseOpen,
      };
    },
  };
</script>
<template>
  <header :class="{ active: isOpen }">
    <div :class="['container', { 'mr-0': isOpen }]">
      <Logo :isOpen="isOpen" :HandCloseOpen="HandCloseOpen" />
      <NavBar
        :isOpen="isOpen"
        :HandIsOpen="HandIsOpen"
        :HandCloseOpen="HandCloseOpen"
      />
    </div>
  </header>
</template>
<style lang="scss" scoped>
  header {
    width: 100%;
    position: fixed;
    z-index: 10;
    top: 0;
    @media (min-width: 1200px) {
      border-bottom: 1px solid #e5e5e5;
    }
  }
  header .container {
    max-width: 1200px;
    margin-left: auto;
    margin-right: auto;
    padding: 8px;
    background-color: #fff;
    &.mr-0 {
      margin-right: 0;
    }
    @media (min-width: 1200px) {
      padding: 24px 45px;

      display: flex;
      justify-content: space-between;
      align-items: center;
    }
  }
  header.active {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    backdrop-filter: blur(4px);
    z-index: 20000;
    background-color: rgba(0, 0, 0, 0.1);
    .container {
      width: 276px;
      right: 0;
      border-radius: 0 0 0 30px;
      background-color: #fff;
    }
  }
</style>
<style lang="scss">
  body {
    padding-top: 80px;
    background-color: #fff;
  }
</style>
