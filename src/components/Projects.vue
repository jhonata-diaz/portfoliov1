<template>
  <section id="projects">
    <AnimateOnVisible name="fadeDown" :duration="1">
      <Title
        class="title"
        :title="content?.object?.metadata?.title || 'Mis proyectos'"
        :description="content?.object?.metadata?.description || 'Estos son algunos de mis proyectos.'"
      />
    </AnimateOnVisible>

    <div class="container-fluid center-block">
      <article class="content text-center">
        <AnimateOnVisible
          class="timeline mx-auto"
          v-for="(post, index) in itemsToShow"
          :key="index"
          name="fadeLeft"
          :duration="0.5"
        >
          <vue-timeline-update
            :date="new Date(post.date)"
            :title="post.title"
            :description="post.content"
            :thumbnail="getImgUrl(post.image)"
            :color="post.color"
            :category="post.tag"
            icon="code"
          />
        </AnimateOnVisible>
      </article>
    </div>
  </section>
</template>

<script>
import Title from "./Title.vue";

export default {
  name: "Projects",
  props: {
    content: {
      type: Object,
      default: () => ({})
    }
  },
  components: { Title },
  data() {
    return {
      defaultItems: [
        {
          date: "2023",
          title: "Administracion de base de datos",
          content: "Creacion de base de datos con herramientas como sqlServer, mysql, postgresql, firebase.",
          image: "databases.png",
          color: "#42b983",
          tag: "db"
        },
        {
          date: "2025",
          title: "Mocroservicios y Docker",
          content: "Desarollo de microservicios de cliente, libros, API gateway en Spring boot con codigo escalable.",
          image: "jdocker.png",
          color: "#42b983",
          tag: "Software"
        },
        {
          date: "2025",
          title: "Aplicacion Android",
          content: "Desarollo de aplicacion android de venta de entradas de musica.",
          image: "musicApp.png",
          color: "#42b983",
          tag: "Android"
        },
        {
          date: "2024",
          title: "Games Opengl",
          content: "Desarollo Game Shoter",
          image: "openglshoter.jpg",
          color: "#ff5722",
          tag: "Game"
        },
        {
          date: "2025",
          title: "Game Engine",
          content: "Desarollo de un Game Engine 3D implementando un diseño Shoter.",
          image: "directxgameshoter.jpg",
          color: "#3f51b5",
          tag: "Game"
        },
        {
          date: "2025",
          title: "Game Multiplayer",
          content: "Desarollo de juego multijugador desarollado en c++ y graficos 3d.",
          image: "multiplayer.jpg",
          color: "#3f51b5",
          tag: "Game"
        },
        {
          date: "2025",
          title: "Games 2D Y 3D",
          content: "Desarollo de juegos en 2d y 3d , space invaders, Juegos de cartas, tower defense, 3d collition Object, terrain world explorer, animaciones 3d, tank game.",
          image: "game2d3d.png",
          color: "#3f51b5",
          tag: "Game"
        }
      ]
    };
  },
  computed: {
    itemsToShow() {
      const items = this.content?.object?.metadata?.items;
      return items && items.length > 0 ? items : this.defaultItems;
    }
  },
  methods: {
    getImgUrl(img) {
      if (!img) return "";
      try {
        return require(`../assets/img/projects/${img}`);
      } catch {
        return ""; // si la imagen no existe, devuelve vacío
      }
    }
  }
};
</script>

<style scoped lang="scss">
@import "@/styles/constants.scss";

$linear: map-get($colors, dark);

#projects {
  background-color: lighten(map-get($colors, primary), 5%);
}

.title {
  color: map-get($colors, light);
}

::v-deep(.text-wrapper) {
  &:after {
    border-bottom: 1px solid map-get($colors, dark);
  }
}

article .inner {
  position: relative;
  display: inline-block;
  vertical-align: middle;
  z-index: 1;
}

.content {
  color: map-get($colors, light);
  margin-top: 30px;
  header {
    height: 100%;
    width: 70%;
  }
  h1 {
    font-size: 3rem;
  }
}

.vertical-center {
  display: flex;
  align-items: center;
}

h1 {
  margin-top: 10px;
  margin-bottom: 20px;
}
</style>
