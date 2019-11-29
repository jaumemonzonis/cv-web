<template>
  <div id="app">
    <Navbar></Navbar>
    <Home></Home>
    <About></About>
    <Experiencia></Experiencia>
    <div class="loader"></div>
  </div>
</template>

<script>
import Home from "./components/Home";
import Navbar from "./components/Navbar";
import About from "./components/About";
import Experiencia from "./components/Experiencia";


export default {
  components: {
    Home,
    Navbar,
    About,
    Experiencia
  },
  methods: {  
     onWindowLoad() {
         $('div.loader').fadeOut();


        },

  },
  created() {
   
    window.addEventListener("load", this.onWindowLoad);
  }

  
};

 

</script>

<style lang="scss">
* {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}

html {
  height: 100%;
}

body {
  margin: 0;
  padding: 0;
  font-family: "Source Sans Pro", sans-serif;
  font-size: 15px;
  font-weight: 400;
  line-height: 1.75;
  letter-spacing: 1px;
  height: 100%;
}

//glitch effect

@mixin glitchCopy {
  content: attr(data-text);
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

@mixin glitchPosition($top, $left) {
  top: $top;
  left: $left;
}

.glitch {
  letter-spacing: 0.1em;

  &:hover {
    position: relative;
    animation: glitch-skew 1s infinite linear alternate-reverse;

    &::before {
      @include glitchCopy;
      @include glitchPosition(0px,2px);
      //left: 2px;
      text-shadow: -2px 0 #48ff00;

      clip: rect(44px, 450px, 56px, 0);
      animation: glitch-anim 3s infinite linear alternate-reverse;
    }

    &::after {
      @include glitchCopy;
       @include glitchPosition(0px,-2px);
      //left: -2px;
      text-shadow: -2px 0 #48ff00, 2px 2px #ff00c1;
      animation: glitch-anim2 1s infinite linear alternate-reverse;
    }
  }
}

.loader {
    position: fixed;
    left: 0px;
    top: 0px;
    width: 100%;
    height: 100%;
    z-index: 9999;
  background: url("./assets/jaume_monzonis.png") 50% 50% no-repeat rgb(249,249,249);
    opacity: .8;
}

@keyframes glitch-anim {
  $steps: 20;
  @for $i from 0 through $steps {
    #{percentage($i*(1/$steps))} {
      clip: rect(random(100) + px, 9999px, random(100) + px, 0);
    }
  }
}

@keyframes glitch-anim2 {
  $steps: 20;
  @for $i from 0 through $steps {
    #{percentage($i*(1/$steps))} {
      clip: rect(random(100) + px, 9999px, random(100) + px, 0);
    }
  }
}
@keyframes glitch-skew {
  $steps: 10;
  @for $i from 0 through $steps {
    #{percentage($i*(1/$steps))} {
    }
  }
}
</style>