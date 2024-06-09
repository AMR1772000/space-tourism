<template>
  <div class="h-screen bg-home bg-home-mobile overflow-hidden">
    <div
      class="content flex relative top-[30%] left-[11%] gap-16 xs:gap-10 xs:flex-col xs:top-[15%] xs:left-[5%] xs:w-[90%] xs:justify-center xs:items-center"
    >
      <div
        class="flex flex-col text-start w-[40%] xs:w-full xs:text-center xs:px-1 xs:gap-2"
      >
        <h1
          class="text-[#D0D6f9] text-[28px] leading-6 tracking-widest xs:text-[20px]"
        >
          SO, YOU WANT TO TRAVEL TO
        </h1>
        <main class="text-white text-[150px] tracking-widest xs:text-[100px]">
          SPACE
        </main>
        <p class="text-[#D0D6f9] pr-5 xs:pr-0 xs:text-base">
          Let’s face it; if you want to go to space, you might as well genuinely
          go to outer space and not hover kind of on the edge of it. Well sit
          back, and relax because we’ll give you a truly out of this world
          experience!
        </p>
      </div>
      <div
        class="flex justify-center items-center border-hover w-[400px] xs:w-[280px] xs:h-[280px] border-hover-mobile"
      >
        <router-link
          class="flex justify-center items-center text-black bg-white text-[50px] w-[250px] h-[250px] rounded-[50%] font-light shadow-2xl xs:w-[200px] xs:h-[200px] xs:text-[35px]"
          to="/destination"
          >Explore</router-link
        >
      </div>
    </div>
  </div>
</template>

<script setup></script>

<style scoped>
.bg-home {
  background-image: url("../assets/images/home/background-home-desktop.jpg");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
}

@media (max-width: 575px) {
  .bg-home-mobile {
    background-image: url("../assets/images/home/background-home-mobile.jpg");
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
  }
}

.border-hover:hover {
  border: 70px solid;
  border-color: rgba(0, 0, 0, 0.4);
  border-radius: 50%;
  transition: all 0.5s ease;
}

@media (max-width: 575px) {
  .border-hover-mobile:hover {
    border: 40px solid;
    border-color: rgba(0, 0, 0, 0.4);
    border-radius: 50%;
    transition: all 0.5s ease;
  }
}
</style>
