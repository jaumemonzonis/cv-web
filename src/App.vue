<template>
  <div id="app">
    <Navbar></Navbar>
    <Home></Home>
    <About></About>
    <Experiencia></Experiencia>
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
    Experiencia,
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

.glitch {
  	letter-spacing: .1em;
  
&:hover {
	position: relative;
	animation: glitch-skew 1s infinite linear alternate-reverse;
	
	&::before{
		@include glitchCopy;
		left: 2px;
		text-shadow: -2px 0 #48ff00;

		clip: rect(44px, 450px, 56px, 0);
		animation: glitch-anim 5s infinite linear alternate-reverse;
	}
	
	&::after {
		@include glitchCopy;
		left: -2px;
		text-shadow: -2px 0 #48ff00, 2px 2px #ff00c1;
		animation: glitch-anim2 1s infinite linear alternate-reverse;
	}
}
}

@keyframes glitch-anim {
  $steps: 20;
  @for $i from 0 through $steps {
    #{percentage($i*(1/$steps))} {
      clip: rect(random(100)+px, 9999px, random(100)+px, 0);

    }
  }
}

@keyframes glitch-anim2 {
  $steps: 20;
  @for $i from 0 through $steps {
    #{percentage($i*(1/$steps))} {
      clip: rect(random(100)+px, 9999px, random(100)+px, 0);
			
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