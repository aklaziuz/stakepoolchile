<template>
  <div>
    <ul class="list">
      <!-- The unordered list element requires a list item element. -->
      <li>
        <!-- Each anchor tag will be inside a list item element. -->
        <a href="../pages/MiUsuario.vue" class="link letras">Home</a>
      </li>
      <li>
        <a href="#" class="link letras">Quienes Somos</a>
      </li>
      <li>
        <a href="#" class="link letras">Contacto</a>
      </li>
    </ul>
    <!-- <v-btn
      color="transparent"
      icon="mdi-domain"
      size="x-large"
      @click.stop="enviarCerrar"
    ></v-btn> -->
  </div>
</template>

<script>
import { gsap } from "gsap";
export default {
  data() {
    return {};
  },
  mounted() {},
  methods: {
    enviarCerrar() {
      this.$emit("cerrarMenu");
    },
    mover() {
      const tl = gsap.timeline();
      tl.from(
        "li",
        {
          duration: 0.75,
          x: 300,
          autoAlpha: 0,
          ease: "elastic.out(1, 1)",
          stagger: {
            each: 0.75,
            amount: 0.5,
          },
        },
        "+=0.25"
      );
      // eslint-disable-next-line no-console
      console.log("derty");
    },
  },
};
</script>
<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Abril+Fatface&family=Arya:wght@700&family=Comfortaa:wght@300&family=Commissioner:wght@800&family=Gowun+Dodum&family=Josefin+Slab:wght@500&family=Poiret+One&family=Poppins:ital,wght@1,700&family=Ubuntu:wght@300&display=swap");

.letras {
  font-family: "Commissioner", sans-serif;
  /* height: 100vh; */
  /* background-color: #1f2d3a; */
  font-size: 100px;
  display: grid;
  place-content: center;
  color: white;
}

.list {
  list-style: none;
  text-align: left;
  padding-left: 5rem;
}
.link {
  display: inline-block;
  margin-block: 2px;
  text-decoration: none;
  position: relative;
}
.link::after {
  content: "";
  width: 100%;
  height: 5px;
  background-color: #2ecdca;
  border-radius: 4px;
  position: absolute;
  left: 0;
  bottom: 0;
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.25s ease;
}
.link:hover::after {
  transform: scaleX(1);
}
</style>
