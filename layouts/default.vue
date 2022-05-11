<template>
  <div>
    >

    <v-app-bar absolute color="transparent" flat>
      <v-toolbar-title>Chile Stake Po</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-app-bar-nav-icon @click.stop="cerrar"></v-app-bar-nav-icon>

      <v-btn icon @click.stop="cerrar2">
        <v-icon>mdi-repeat</v-icon>
      </v-btn>
    </v-app-bar>

    <!-- <div class="cardano grande">Cardano</div> -->

    <v-container style="height: auto">
      <Nuxt />
    </v-container>

    <v-navigation-drawer
      v-model="drawer"
      color="transparent"
      style="width: 95%; height: 95%; margin: 30px 0px 0px 30px"
      class="container"
      transition="v-slide-x-transition"
      absolute
      temporary
      app
      ><menufondo ref="refcomfondo" @cerrarMenu="cerrar"> </menufondo>
    </v-navigation-drawer>

    <v-navigation-drawer
      v-model="drawer2"
      transition="fade-transition"
      color="transparent"
      style="width: 95%; height: 95%; margin: 30px 0px 0px 30px"
      class="container"
      absolute
      temporary
      right
      app
      ><authfondo></authfondo>
    </v-navigation-drawer>
    <v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </div>
</template>
<script>
import { gsap } from "gsap";
import menufondo from "~/components/menu-fondo.vue";
import authfondo from "~/components/AuthFondo.vue";

export default {
  name: "DefaultLayout",
  components: { menufondo, authfondo },

  data() {
    return {
      drawer: false,
      drawer2: false,
      controlaAbierto: false,
    };
  },
  mounted() {
    /*  window.addEventListener("scroll", this.handleScroll); */

    /*  gsap.fromTo(
      ".cardano",
      {
        duration: 4,
        opacity: 0,
        x: "5%",
      },
      { duration: 1.5, opacity: 1, x: 0, ease: "power3.inOut", delay: 2 }
    ); */
    const tl = gsap.timeline();
    tl.from(".cardano", {
      duration: 2,
      ease: "elastic.out(1, 0.3)",
      yoyo: true,
      y: 500,
      x: -300,
    });
    /* tl.to(".cardano", { delay:2,duration: 1, ease: "elastic.out(1, 0.3)",  , yoyo:true}); */
    tl.to(".cardano", {
      delay: 1.5,
      duration: 1,
      y: 20,
      repeat: -1,
      yoyo: true,
    });
    /*  gsap.fromTo(
      ".cardano",
      {
        duration: 2,
        opacity: 0,
        x: "-100%",
      },
      { duration: 1.5, opacity: 1, x: 0, ease: "power3.inOut", delay: 0.5 }
    );   */
  },
  methods: {
    cerrar() {
      this.drawer = !this.drawer;
      this.activar();
    },

    cerrar2() {
      this.drawer2 = !this.drawer2;
    },

    activar() {
      this.$refs.refcomfondo.mover();
      // eslint-disable-next-line no-console
      console.log("activado");
    },
  },
};
</script>
<style>
@import url("https://fonts.googleapis.com/css2?family=Arya:wght@700&family=Comfortaa:wght@300&family=Gowun+Dodum&family=Josefin+Slab:wght@500&family=Poiret+One&family=Ubuntu:wght@300&display=swap");

.cardano {
  font-family: "Comfortaa", cursive;
  color: antiquewhite;
}
.grande {
  font-size: 100px;
}

.chica {
  font-size: 30px;
}
.derty {
  width: 1000px;
  height: 10px;
  background-color: red;
}

.poner {
  margin: 20px 30px 50px 30px;
}
.arriba {
  margin-top: 100px;
}

.container {
  /*  background-color: rgba(255, 255, 255, 0.1);
   height: 95%;
  backdrop-filter: blur(30 px);
  border: solid 1px rgba(255, 255, 255, 0.5);
  border-radius: 5px; */
  /* width: 95%; */
  /* margin: 0 auto; */

  box-shadow: 0 0 1rem 0 rgba(0, 0, 0, 0.2);
  border-radius: 5px;
  background-color: rgba(255, 255, 255, 0.08);
  border: solid 1px rgba(255, 255, 255, 0.5);
  backdrop-filter: blur(18px);
}
</style>
