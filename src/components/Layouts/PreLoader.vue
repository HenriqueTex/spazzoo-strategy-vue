<template>
  <div id="preloader" v-if="isLoading">
    <div class="preloader">
      <div class="waviy">
        <span>S</span>
        <span>P</span>
        <span>A</span>
        <span>Z</span>
        <span>Z</span>
        <span>O</span>
        <span>O</span>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "PreLoader",
  data() {
    return {
      isLoading: true,
    };
  },
  mounted() {
    setTimeout(() => {
      this.isLoading = false;
    }, 2000);
  },
});
</script>

<style lang="scss">
#preloader {
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 9999;
  position: fixed;
  background-color: var(--whiteColor);

  .preloader {
    transform: translate(-50%, -50%);
    position: absolute;
    left: 50%;
    top: 50%;

    .loader {
      position: relative;
      overflow: hidden;
      display: block;
      height: 150px;
      width: 150px;
      margin: {
        left: auto;
        right: auto;
      }
      div {
        height: 100%;
      }
    }
    .loader,
    .loader div {
      padding: 8px;
      border-radius: 50%;
      border: 2px solid transparent;
      animation: rotate linear 3.5s infinite;
      border: {
        top-color: var(--mainColor);
        border-bottom: var(--mainColor);
      }
    }
    .waviy {
      margin-top: 20px;
      position: relative;
      text-align: center;
      -webkit-box-reflect: below -47px linear-gradient(transparent, rgba(0, 0, 0, 0.2));
      font: {
        size: 60px;
        weight: 700;
      }
      span {
        position: relative;
        color: var(--headingColor);
        animation-delay: 0.1s;
        display: inline-block;
        animation: waviy 1s infinite;

        &:nth-child(2) {
          animation-delay: 0.2s;
        }
        &:nth-child(3) {
          animation-delay: 0.3s;
        }
        &:nth-child(4) {
          animation-delay: 0.4s;
        }
        &:nth-child(5) {
          animation-delay: 0.5s;
        }
      }
    }
  }
}
@keyframes rotate {
  0% {
    transform: rotate(0deg);
  }
  50% {
    transform: rotate(180deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
@keyframes waviy {
  0%,
  40%,
  100% {
    transform: translateY(0);
  }
  20% {
    transform: translateY(-20px);
  }
}
/* Max width 767px */
@media only screen and (max-width: 767px) {
  #preloader {
    .preloader {
      .waviy {
        font: {
          size: 40px;
        }
      }
    }
  }
}
</style>