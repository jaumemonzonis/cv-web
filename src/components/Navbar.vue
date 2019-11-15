<template>
  <b-navbar toggleable="lg" type="dark">
    <b-navbar-toggle target="nav-collapse" class="custom-toggler"></b-navbar-toggle>
    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav class>
        <b-nav-item href="#" class="item" :class="{'item-black':! showBlack}">SOBRE MI</b-nav-item>
        <b-nav-item href="#" class="item" :class="{'item-black':! showBlack}">EXPERIENCIA</b-nav-item>
        <b-nav-item href="#" class="item" :class="{'item-black':! showBlack}">EDUCACIÓN</b-nav-item>
        <b-nav-item href="#" class="item" :class="{'item-black':! showBlack}">HABILIDADES</b-nav-item>
        <b-nav-item href="#" class="item" :class="{'item-black':! showBlack}">IDIOMAS</b-nav-item>
        <b-nav-item href="#" class="item" :class="{'item-black':! showBlack}">CONTACTO</b-nav-item>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</template>

<script>
import $ from 'jquery';
export default {
  data() {
      var home = ('.home');
      console.log(home.clientHeight);
    return {
      showBlack: true,
      lastScrollPosition: 0,
    };
  },
  mounted() {
    window.addEventListener("scroll", this.onScroll);
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.onScroll);
  },
  methods: {
    onScroll() {
      
      var home =  $('.home');
      console.log(home.height());
      const currentScrollPosition =
        window.pageYOffset || document.documentElement.scrollTop;
      if (currentScrollPosition < 0) {
        return;
      }
      // Stop executing this function if the difference between
      // current scroll position and last scroll position is less than some offset
      if (Math.abs(currentScrollPosition - this.lastScrollPosition) < home.height()) {
        return;
      }
    

      this.showBlack = currentScrollPosition < this.lastScrollPosition;
      this.lastScrollPosition = currentScrollPosition;
    }
  }
};
</script>

<style lang="scss" scoped>
.navbar {
  width: 100%;
  padding: 6px 0;
  position: fixed;
  top: 0;
  left: 0;
  background-color: transparent;
  z-index: 20;
  @media screen and (min-width: 768px) {
    padding: 20px 0;
  }
  .navbar-collapse {
    justify-content: flex-end;
    padding-right: 15px;
    padding-left: 15px;
    margin-right: auto;
    margin-left: auto;
  }
  .navbar-nav .item,
  .navbar-nav .item.item-black {
    a {
      position: relative;
      font-size: 13px;
      font-weight: 700;
      color: #ddd;
      display: block;
      padding: 10px 15px;

      @media (min-width: 768px) {
        padding-top: 15px;
        padding-bottom: 15px;
      }
    }
  }
  .navbar-nav > li > a.active {
    background-color: transparent;
  }
  .navbar-nav > li > a:hover {
    background-color: transparent;
    color: #ddd;
  }

  //MOBILE
  .navbar-toggler {
    padding-left: 30px;
  }
  .custom-toggler.navbar-toggler {
    border-color: transparent;
  }
  .custom-toggler .navbar-toggler-icon {
    background-image: url("data:image/svg+xml;charset=utf8,%3Csvg viewBox='0 0 32 32' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath stroke='rgba(221,221,221, 0.7)' stroke-width='2' stroke-linecap='round' stroke-miterlimit='10' d='M4 8h24M4 16h24M4 24h24'/%3E%3C/svg%3E");
  }

  .navbar-nav .item.item-black a {
    color: red;
  }
}
</style>