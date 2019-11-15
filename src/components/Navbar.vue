<template>
  <b-navbar toggleable="lg" type="dark">
    <b-navbar-toggle target="nav-collapse" class="custom-toggler"></b-navbar-toggle>
    <b-collapse id="nav-collapse" is-nav>
      <b-navbar-nav class>
        <b-nav-item href="/#inicio" class="item" @click="animation">INICIO</b-nav-item>
        <b-nav-item href="/#sobremi" class="item" @click="animation">SOBRE MI</b-nav-item>
        <b-nav-item href="/#experiencia" class="item" @click="animation">EXPERIENCIA</b-nav-item>
        <b-nav-item href="#" class="item" @click="animation">EDUCACIÓN</b-nav-item>
        <b-nav-item href="#" class="item" @click="animation">HABILIDADES</b-nav-item>
        <b-nav-item href="#" class="item" @click="animation">IDIOMAS</b-nav-item>
        <b-nav-item href="#" class="item" @click="animation">CONTACTO</b-nav-item>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</template>

<script>
import $ from "jquery";
export default {
  data() {
    return {
      showBlack: true,
      lastScrollPosition: 0
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
      var home = $(".home");
      var item = $(".item");
      //detectar scroll hacia abajo
      var obj = $(window); //objeto sobre el que quiero detectar scroll
      var obj_top = obj.scrollTop(); //scroll vertical inicial del objeto
      obj.scroll(function() {
        var obj_act_top = $(this).scrollTop(); //obtener scroll top instantaneo

        if (obj_act_top > obj_top) {
          if (obj_act_top >= home.height()) {
            item.addClass("item-black");
          }  
          } if (obj_act_top < obj_top) { 
            if (obj_top < home.height()) {
              item.removeClass("item-black");
            }
        }
    
        obj_top = obj_act_top; //almacenar scroll top anterior
      });
    },
    animation() {
      $('a[href^="#"]').click(function() {
        var destino = $(this.hash);
        if (destino.length == 0) {
          destino = $('a[name="' + this.hash.substr(1) + '"]');
        }
        if (destino.length == 0) {
          destino = $("html");
        }
        $("html, body").animate({ scrollTop: destino.offset().top }, 200);
        return false;
      });
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
    color: black;
  }
}
</style>