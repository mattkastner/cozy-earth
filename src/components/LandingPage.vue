<template>
  <div class="main-bg">
    <div class="main-bg--marroon"></div>
    <div class="main-bg--forest"></div>
  </div>
  <div v-if="showDetail != 'none'" class="pop-up__overlay">
    <div class="pop-up__container">
      <div class="pop-up" :class="menuType">
        <div class="info" :class="menuTextType">
          <svg @click="handleExit" xmlns="http://www.w3.org/2000/svg" class="exit-icon" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
            <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
          </svg>
          <div class="horizontal-row"></div>
          <h1 class="info-h1"><span>E</span>xplore</h1>
          <div class="horizontal-row--thin"></div>
          <p>
            Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae
            vitae dicta sunt explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt. Neque
            porro quisquam est, qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat
            voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur?
          </p>
          <button>READ MORE</button>
        </div>
      </div>
    </div>
  </div>
  <div class="main-hero">
    <div class="text-container" :class="heroType">
      <h1><span>E</span>xplore</h1>
    </div>
    <div class="more-details">
      <div class="plus-circle" @click="handleButtonDetails" :class="buttonType">
        <svg xmlns="http://www.w3.org/2000/svg" class="exit-icon" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
          <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
        </svg>
      </div>
      <p class="more-details--p" v-if="showDetail != 'showMenu'" :class="heroType">More Details</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "LandingPage",
  components: {},
  data: function () {
    return {
      showDetail: "none",
    };
  },
  computed: {
    buttonType() {
      const types = { none: "", showMenu: "plus-circle--animate-vanish", hideMenu: "plus-circle--animate-show" };
      return types[this.showDetail];
    },
    menuType() {
      const types = { none: "", showMenu: "pop-up--animate-showMenu", hideMenu: "pop-up--animate-hideMenu" };
      return types[this.showDetail];
    },
    menuTextType() {
      const types = { none: "", showMenu: "info--animate-showMenuText", hideMenu: "info--animate-hideMenuText" };
      return types[this.showDetail];
    },
    heroType() {
      const types = { none: "", showMenu: "text-container--hide", hideMenu: "text-container--show" };
      return types[this.showDetail];
    },
  },
  methods: {
    handleButtonDetails() {
      console.log("click me");
      this.showDetail = "showMenu";
    },
    handleExit() {
      this.showDetail = "hideMenu";
      let self = this;
      setTimeout(function () {
        console.log("ran");
        self.showDetail = "none";
      }, 400);
    },
  },
};
</script>

<style scoped lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Unna:wght@400&display=swap");

.main-bg {
  position: absolute;
  z-index: -1;
  top: 0;
  left: 0;
  display: flex;
  height: 100vh;
  width: 100vw;
  &--marroon {
    display: none;
    width: 400px;
    height: 100%;
    background-color: #591e1b;
  }
  &--forest {
    background-repeat: no-repeat;
    background-size: cover;
    height: 100%;
    width: 100%;
    background-image: url("../assets/forest.webp");
  }
}

.pop-up__overlay {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 3;
  height: 100vh;
  width: 100vw;
}

.pop-up__container {
  display: flex;
  justify-content: center;
  align-items: center;
}

.pop-up--animate-showMenu {
  animation-name: showMenu;
  animation-fill-mode: forwards;
  animation-duration: 400ms;
}

.pop-up--animate-hideMenu {
  animation-name: hideMenu;
  animation-fill-mode: forwards;
  animation-duration: 350ms;
}

.pop-up {
  position: relative;
  background: white;

  .info--animate-hideMenuText {
    animation-name: hideMenuText;
    animation-fill-mode: forwards;
    animation-duration: 0.3s;
  }

  .info--animate-showMenuText {
    animation-name: showMenuText;
    animation-fill-mode: forwards;
    animation-duration: 1.5s;
    animation-delay: 0.3s;
  }
  .info {
    opacity: 0;
    position: relative;
    padding: 45px 50px;
    right: 0;

    .exit-icon {
      position: absolute;
      top: 14px;
      right: 14px;
      height: 30px;
      width: 30px;
    }

    .horizontal-row {
      margin-left: -4px;
      height: 24px;
      width: 90%;
      background: linear-gradient(90deg, #591e1c 0%, rgba(89, 30, 28, 0) 85.94%);
    }

    h1 {
      margin: 16px 0;
      font-size: 4rem;
      color: #5a1e1b;
    }

    .horizontal-row--thin {
      height: 2px;
      width: 60%;
      background: linear-gradient(90deg, #5a1e1b 0%, rgba(217, 217, 217, 0) 100%);
    }

    p {
      margin-top: 30px;
      font-size: 1rem;
      line-height: 30px;
      color: #626162;
      font-family: sans-serif;
    }

    button {
      margin: 30px 0;
      border: 1px solid #626162;
      font-size: 1rem;
      font-weight: 100 !important;
      color: white;
      padding: 12px 34px;
      background: linear-gradient(90deg, #5a1f1c 0%, #9a6957 100%);
    }
  }
}

.main-hero {
  position: absolute;
  bottom: 30%;
  display: flex;
  justify-content: center;
  font-family: sans-serif;
  max-width: 370px;

  .text-container--hide {
    animation-name: hideText;
    animation-fill-mode: forwards;
    animation-duration: 0.2s;
  }

  .text-container--show {
    animation-name: showText;
    animation-fill-mode: forwards;
    animation-duration: 0.5s;
  }

  .text-container {
    overflow: hidden;
    width: 700px;
    max-width: 90%;
    height: auto;

    h1 {
      right: 0;
      font-family: "Unna", serif;
      font-size: 6rem;
      font-weight: 500;
      color: white;
      margin: 0px;
      span {
        font-size: 10rem;
      }
    }
  }

  .more-details {
    height: 50px;
    width: 200px;
    position: absolute;
    left: 90px;
    bottom: -25px;
    display: flex;
    align-items: center;

    .plus-circle--animate-vanish {
      animation-name: vanish;
      animation-fill-mode: forwards;
      animation-duration: 500ms;
    }

    .plus-circle--animate-show {
      animation-name: show;
      animation-fill-mode: forwards;
      animation-duration: 500ms;
    }

    .plus-circle {
      display: flex;
      align-items: center;
      justify-content: center;
      margin-right: 10px;
      background: white;
      padding: 8px;
      border-radius: 100%;

      .exit-icon {
        transform: rotate(45deg);
        height: 14px;
        width: 14px;
      }
    }
    .more-details--p {
      font-size: 1rem;
      font-weight: 300;
      color: white;
    }
  }
}

@keyframes hideText {
  0% {
    width: 100%;
  }
  60% {
    width: 80%;
  }
  100% {
    width: 0%;
  }
}

@keyframes showText {
  0% {
    opacity: 0;
    width: 0px;
  }
  60% {
    width: 80%;
  }
  100% {
    opacity: 1;
    width: 100%;
  }
}

@keyframes vanish {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(0.7);
  }
  60% {
    transform: scale(0.8);
  }
  100% {
    transform: scale(0);
    display: none;
  }
}

@keyframes show {
  0% {
    transform: scale(0);
    display: none;
  }
  50% {
    transform: scale(0.8);
  }
  60% {
    transform: scale(0.7);
  }
  100% {
    transform: scale(1);
  }
}

@keyframes showMenu {
  0% {
    border-radius: 100%;
    width: 0;
    height: 0;
    transform: translateX(0%);
    transform: translateY(0%);
    top: var(100%, 2px);
  }
  100% {
    width: 100%;
    transform: translateX(100%);
    transform: translateY(100%);
    transform: scale(1);
    border-radius: 2px;
    height: var(100%, 2px);
    top: 0;
  }
}

@keyframes hideMenu {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}

@keyframes showMenuText {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

@keyframes hideMenuText {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
    overflow: hidden;
  }
}

@media (min-width: 850px) {
  .main-hero {
    bottom: 200px;
    left: 170px;
    display: block;
    max-width: 500px;
  }

  .main-hero .text-container h1 {
    font-size: 7.5rem;
  }

  .main-hero .more-details .more-details--p {
    font-size: 1rem;
  }

  .plus-circle {
    padding: 6px;
  }

  .main-bg--marroon {
    display: block;
  }

  .main-bg--forest {
    width: calc(100% - 400px);
  }

  .pop-up__container {
    position: absolute;
    top: 60px;
    width: 40rem;
    height: 650px;
  }

  .pop-up {
    left: 140px;
    bottom: 0px;
  }

  .main-hero .text-container h1 {
    max-width: 500px;
  }
}
</style>
