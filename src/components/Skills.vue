<template>
  <section id="skills">
    <AnimateOnVisible name="fadeDown" :duration="1">
      <Title
        :title="content?.object?.metadata?.title || 'Habilidades'"
        :description="content?.object?.metadata?.description || 'Éstas son algunas de mis habilidades.'"
      />
    </AnimateOnVisible>

    <div class="section-content">
      <div class="container-fluid">
        <div class="row d-flex flex-wrap align-items-center">
          <div
            class="col-md-2 m-auto pb-4"
            v-for="(post, index) in itemsToShow"
            :key="index"
          >
            <AnimateOnVisible name="bounce">
              <img
                id="imgLogo"
                class="img-responsive mx-auto d-block"
                :src="getImgUrl(post.img)"
                :alt="post.title"
              />
              <div id="divAlt" class="altCaption text-center">{{ post.title }}</div>
            </AnimateOnVisible>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import Title from "./Title.vue";

export default {
  name: "Skills",
  components: { Title },
  props: {
    content: {
      type: Object,
      default: () => ({})
    }
  },
  data() {
    return {
      defaultItems: [
        { img: "C.png", title: "C" },
        { img: "cplusplus.png", title: "C++" },
        { img: "Csharp_Logo.png", title: "C#" },
        { img: "java.png", title: "Java" },
        { img: "Kotlin_Icon.png", title: "Kotlin" },
        { img: "dbdata.png", title: "Bases de datos" },
        { img: "azure.png", title: "Azure" },
        { img: "Unreal_Engine_Logo.svg.png", title: "Unreal" },
        { img: "Octocat.png", title: "Git/Github" },
        { img: "trello-seeklogo.png", title: "Trello" },
        { img: "linux.png", title: "Linux" }
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
        return require(`../assets/img/logo/${img}`);
      } catch {
        return ""; // si la imagen no existe, devuelve vacío
      }
    }
  }
};
</script>

<style scoped lang="scss">
@import "@/styles/constants.scss";

#skills {
  background-color: lighten(map-get($colors, dark), 100%);
}

@media (min-width: #{map-get($breakpoints, medium)}) {
  .section-content {
    width: 80%;
    margin: 0 auto;
  }
}

img {
  max-width: 120px;
}

.altCaption {
  color: map-get($colors, secondary);
  margin-top: 1rem;
}
</style>
