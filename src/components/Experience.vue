<template> 
  <section id="experience">
    <AnimateOnVisible name="fadeDown" :duration="1">
      <Title
        class="title"
        :title="content?.object?.metadata?.title || 'Experiencia'"
        :description="content?.object?.metadata?.description || 'Profesional y Academico'"
      />
    </AnimateOnVisible>

    <AnimateOnVisible name="fadeUp" :duration="1">
      <div class="container-fluid">
        <div class="row">
          <ExperienceColumn
            :posts="content?.object?.metadata?.academic || defaultAcademic"
            title="Formacion"
            class="col-12 col-md left"
          />
          <ExperienceColumn
            :posts="content?.object?.metadata?.professional || defaultProfessional"
            title="Profesional"
            class="col-12 col-md right"
          />
        </div>
      </div>
    </AnimateOnVisible>
  </section>
</template>

<script>
import Title from "./Title.vue";
import ExperienceColumn from "./ExperienceColumn.vue";

export default {
  name: "Experience",
  props: {
    content: {
      type: Object,
      default: () => ({})
    }
  },
  components: { Title, ExperienceColumn },
  data() {
    return {
      defaultAcademic: [
        {
          year: "2020 - 2025",
          title: "Licenciatura en Informatica",
          content: "Universidad Catolica Boliviana San Pablo, Bolivia."
        },
        {
          year: "2018 - 2019",
          title: "Licenciatura en Medicina",
          content: "Universidad Mayor de San Simon, Bolivia."
        }
      ],
      defaultProfessional: [
        {
          year: "2024",
          title: "Bases de datos SQL",
          content: "Desarollo de bases de datos de imobiliaria en SqlServer."
        },
         {
          year: "2025",
          title: "Microservicios",
          content: "Desarollo de microservicios con lenguaje java y mysql."
        },
         {
          year: "2025",
          title: "Aplicaciones Android",
          content: "Desarollo de aplicaciones android con Kotlin, Jetpack Compose y firebase."
        },
        {
          year: "2020 - 2023",
          title: "Games en 2D y 3D",
          content: "Desarollo de videojuegos en 2d y 3d con lenguaje c++, usando librerias avanzadas."
        },
        {
          year: "2024 - 2025",
          title: "3D Engine Game",
          content: "Desarollo de mi propio engine con c++ y directx, incluyendo mecanicas avanzadas."
        }
      ]
    };
  }
};
</script>

<style scoped lang="scss">
@import "@/styles/constants.scss";

$linear: map-get($colors, dark);

#experience {
  background-color: lighten(map-get($colors, primary), 5%);
}

.title {
  color: map-get($colors, light);
}

.row {
  padding-top: 20px;
  text-align: center;
}

@media (min-width: #{map-get($breakpoints, small)}) {
  .left {
    text-align: right;
    border-right: 2px solid $linear;
  }
  .right {
    text-align: left;
  }
}

@media (max-width: #{map-get($breakpoints, small)}) {
  .right {
    margin-top: 20px;
  }
  .left:before {
    content: "";
    position: absolute;
    left: 20%;
    bottom: 0;
    height: 2px;
    width: 60%;
    border-bottom: 2px solid $linear;
  }
}

::v-deep(.text-wrapper) {
  &:after {
    border-bottom: 1px solid map-get($colors, dark);
  }
}
</style>
