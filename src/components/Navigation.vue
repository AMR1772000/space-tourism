<template>
  <div>
    <!-- Mobile Navbar -->
    <div class="mobile-nav absolute top-[5%] left-[85%]" @click="toggleSidebar">
      <img
        src="../assets/images/icon-hamburger.svg"
        alt="Logo"
        class="text-white w-[40px] h-[30px]"
      />
    </div>
    <!-- Sidebar for Mobile -->
    <div v-if="isSidebarVisible" class="sidebar">
      <div class="flex justify-end w-full items-end mt-3 mb-8">
        <img
          src="../assets/images/icon-close.svg"
          alt="close icon"
          @click="toggleSidebar"
          class="w-[25px] h-[25px]"
        />
      </div>

      <router-link
        class="nav-link w-full"
        :class="{ 'active-link': $route.path === '/' }"
        to="/"
        ><span class="font-semibold mr-2">00</span> HOME</router-link
      >
      <router-link
        class="nav-link w-full"
        :class="{ 'active-link': $route.path === '/destination' }"
        to="/destination"
        ><span class="font-semibold mr-2">01</span> DESTINATION</router-link
      >
      <router-link
        class="nav-link w-full"
        :class="{ 'active-link': $route.path === '/crew' }"
        to="/crew"
        ><span class="font-semibold mr-2">02</span> CREW</router-link
      >
      <router-link
        class="nav-link w-full"
        :class="{ 'active-link': $route.path === '/technology' }"
        to="/technology"
        ><span class="font-semibold mr-2">03</span> TECHNOLOGY</router-link
      >
    </div>

    <!-- Desktop Navbar -->
    <div class="desktop-nav">
      <div
        class="w-[38%] bg-[#344345] h-[2px] flex z-10 absolute left-[10%] top-[8%]"
      ></div>
      <div
        class="text-white flex gap-7 items-center justify-center w-[52%] float-end mt-5 text-[20px] absolute top-[0%] left-[48%]"
        :class="{
          'Home-navbar': $route.path === '/',
          'other-navbar':
            $route.path === '/destination' ||
            $route.path === '/crew' ||
            $route.path === '/technology',
        }"
      >
        <router-link
          class="nav-link"
          :class="{ 'active-link': $route.path === '/' }"
          to="/"
          ><span class="font-semibold">00</span> Home</router-link
        >
        <router-link
          class="nav-link"
          :class="{ 'active-link': $route.path === '/destination' }"
          to="/destination"
          ><span class="font-semibold">01</span> Destination</router-link
        >
        <router-link
          class="nav-link"
          :class="{ 'active-link': $route.path === '/crew' }"
          to="/crew"
          ><span class="font-semibold">02</span> Crew</router-link
        >
        <router-link
          class="nav-link"
          :class="{ 'active-link': $route.path === '/technology' }"
          to="/technology"
          ><span class="font-semibold">03</span> Technology</router-link
        >
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const isSidebarVisible = ref(false);

const toggleSidebar = () => {
  isSidebarVisible.value = !isSidebarVisible.value;
};
</script>

<style scoped>
.Home-navbar {
  background-image: linear-gradient(to right, #1b2122, #4b5378, #1c2038);
  opacity: 0.7;
}
.other-navbar {
  background-image: linear-gradient(to right, #424242, #3b3b3b, #2c2c2c);
  opacity: 0.6;
}
.nav-link {
  padding-bottom: 1rem;
  position: relative;
  margin-top: 20px;
  transition: all 0.1s ease;
}
.nav-link:hover {
  border-bottom: 4px solid gray;
}
.active-link {
  border-bottom: 4px solid white;
}
/* Mobile styles */
.mobile-nav {
  display: none;
}
.desktop-nav {
  display: flex;
}

/* Media query for mobile devices */
@media (max-width: 975px) {
  .mobile-nav {
    display: flex;
    align-items: center;
  }
  .desktop-nav {
    display: none;
  }
}

/* Sidebar styles */
.sidebar {
  position: absolute;
  border-radius: 12px 0 12px 0;
  top: 0;
  right: 0;
  width: 70%;
  height: 100%;
  background-image: linear-gradient(to bottom, #090e16, #141722, #181a29);

  color: white;
  padding: 20px 30px 20px 30px;
  display: flex;
  flex-direction: column;
  align-items: start;
  z-index: 20;
}
</style>
