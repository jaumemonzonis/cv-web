<template>
  <div class="home" id="#inicio">
    <b-container>
      <b-row align-v="center" align-h="center">
        <b-col cols="6" class="blockimage">
          <div class="blockimage__img">
            <img src="../assets/jaume_monzonis.png" />
          </div>
        </b-col>
        <b-col cols="6" class="blockpresentation">
          <h1 class="blockpresentation__name glitch" data-text="
JAUME MONZONIS LÁZARO">JAUME MONZONIS LÁZARO</h1>
          <h1>
            <span class="blockpresentation__job">{{ typeValue }}</span>
            <span class="blockpresentation__cursor" :class="{'typing': typeStatus}">&nbsp;</span>
          </h1>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      typeValue: "",
      typeStatus: false,
      typeArray: ["Desarrollador Front-End", "Javascript", "Vue", "Wordpress"],
      typingSpeed: 100,
      erasingSpeed: 50,
      newTextDelay: 1000,
      typeArrayIndex: 0,
      charIndex: 0
    };
  },
  methods: {
    typeText() {
      if (this.charIndex < this.typeArray[this.typeArrayIndex].length) {
        if (!this.typeStatus) this.typeStatus = true;
        this.typeValue += this.typeArray[this.typeArrayIndex].charAt(
          this.charIndex
        );
        this.charIndex += 1;
        setTimeout(this.typeText, this.typingSpeed);
      } else {
        this.typeStatus = false;
        setTimeout(this.eraseText, this.newTextDelay);
      }
    },
    eraseText() {
      if (this.charIndex > 0) {
        if (!this.typeStatus) this.typeStatus = true;
        this.typeValue = this.typeArray[this.typeArrayIndex].substring(
          0,
          this.charIndex - 1
        );
        this.charIndex -= 1;
        setTimeout(this.eraseText, this.erasingSpeed);
      } else {
        this.typeStatus = false;
        this.typeArrayIndex += 1;
        if (this.typeArrayIndex >= this.typeArray.length)
          this.typeArrayIndex = 0;
        setTimeout(this.typeText, this.typingSpeed + 1000);
      }
    }
  },
  created() {
    setTimeout(this.typeText, this.newTextDelay + 200);
  }
};
</script>

<style lang="scss" scoped>
.home {
  background-color: black;
  color: white;
  height: 100vh;
  .container {
    height: 100%;
    .row {
      height: 100%;
      flex-direction: column;
      .col-6:first-child {
        display: flex;
        justify-content: center;
        align-items: flex-end;
      }
      .blockpresentation {
        display: flex;
        flex-direction: column;
        justify-content: flex-start;
        align-items: center;
        padding-top: 30px;
        .blockpresentation__name {
          text-align: center;
          font-size: 34px;
        }
        .blockpresentation__job {
          text-align: center;
          font-size: 28px;
        }
        .blockpresentation__cursor {
          display: inline-block;
          margin-left: 3px;
          width: 4px;
          background-color: #fff;
          animation: cursorBlink 1s infinite;
          &.typing {
            animation: none;
          }
        }
      }
      .blockimage {
        .blockimage__img {
          -webkit-border-radius: 50%;
          -moz-border-radius: 50%;
          border-radius: 50%;
          &:hover {
            $url: url("../assets/jaume_monzonis.png");
            $offset: 5px;
            background-image: $url;
            background-size: cover;
            background-position: center;
            @supports (mix-blend-mode: multiply) {
              position: relative;
              overflow: hidden;
              background-color: magenta;
              background-blend-mode: screen;
              &:before,
              &:after {
                display: block;
                content: "";
                position: absolute;
                top: 0;
                left: 0;
                right: 0;
                bottom: 0;
                background: inherit;
                mix-blend-mode: multiply;
                transform: scale(1);
                animation: moving 2s steps(20, end) infinite;
              }
              &:before {
                background-color: yellow;
                background-blend-mode: screen;
                transform-origin: top left;
              }
              &:after {
                background-color: cyan;
                background-blend-mode: screen;
                transform-origin: bottom right;
              }
            }
          }
          img {
        
          -webkit-border-radius: 50%;
          -moz-border-radius: 50%;
          border-radius: 50%;
          -webkit-box-shadow: 0 4px 8px rgba(0, 0, 0, 0.52);
          -moz-box-shadow: 0 4px 8px rgba(0, 0, 0, 0.52);
          box-shadow: 0 4px 8px rgba(0, 0, 0, 0.52);
          }
        }
      }
    }
  }
}
@keyframes moving {
  @for $i from 1 through 20 {
    #{$i*5}% {
      transform: scale(1 - (random(8)-4)/100)
        translate((random(20) - 10) * 1px, (random(20) - 10) * 1px);
    }
  }
}
[class$="-effect"] img {
  vertical-align: top !important;
  margin: 0 !important;
  opacity: 0 !important;
}
@keyframes cursorBlink {
  49% {
    background-color: #fff;
  }
  50% {
    background-color: transparent;
  }
  99% {
    background-color: transparent;
  }
}
</style>