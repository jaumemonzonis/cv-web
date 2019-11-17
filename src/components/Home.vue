<template>
  <div class="home" id="#inicio">
    <b-container>
      <b-row align-v="center" align-h="center">
        <b-col cols="6" class="blockimage">
          <img src="../assets/logo.png" class="blockimage__img" alt="Foto_JaumeMonzonisLazaro" />
        </b-col>
        <b-col cols="6" class="blockpresentation">
          <h1 class="blockpresentation__name">JAUME MONZONIS LÁZARO</h1>
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
      typingSpeed: 200,
      erasingSpeed: 100,
      newTextDelay: 2000,
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
  }
}

  @keyframes cursorBlink {
    49% { background-color: #fff; }
    50% { background-color: transparent; }
    99% { background-color: transparent; }
  }}
</style>