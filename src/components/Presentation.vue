<template> 
  <div class="paragraph">
    <h3>{{ safeContent.pres_title }}</h3>
    <div class="begin">{{ safeContent.pres_first }}</div>
    <p>{{ safeContent.pres_second }}</p>
  </div>
</template>

<script>
export default {
  name: 'Description',
  props: {
    content: {
      type: Object,
      default: () => ({})
    }
  },
  computed: {
    safeContent() {
      return {
        pres_title: this.content?.object?.metadata?.pres_title || 'Presentación',
        pres_first: this.content?.object?.metadata?.pres_first || 'Hola soy Jhonatan Gustavo Diaz Choque, software developer.',
        pres_second: this.content?.object?.metadata?.pres_second || 'Soy un Desarrollador de Software con experiencia en la construcción de aplicaciones escalables, arquitecturas de microservicios y desarrollo de bases de datos. Además, cuento con conocimientos en redes informáticas y en el desarrollo de videojuegos, incluyendo la creación de motores y experiencias interactivas. La tecnología ha sido mi pasión desde muy joven y sigue siendo el motor que me impulsa cada día. Siempre me ha gustado involucrarme en proyectos que me saquen de mi zona de confort, ya sea diseñando sistemas backend complejos, optimizando bases de datos o experimentando con motores de videojuegos. Esta curiosidad y perseverancia me han permitido ser autodidacta, adaptable y orientado a resolver problemas, superando las dificultades y aprendiendo de cada desafío. Actualmente, me encuentro en búsqueda de nuevas oportunidades y retos que me permitan aprovechar mis habilidades en el desarrollo de software, explorar tecnologías innovadoras y contribuir en proyectos con impacto.'
      }
    }
  }
}
</script>


<style scoped lang="scss">
@import '@/styles/constants.scss';

.paragraph {
  color: map-get($colors, primary);
  .begin {
    color: map-get($colors, secondary);
  }
}
</style>
