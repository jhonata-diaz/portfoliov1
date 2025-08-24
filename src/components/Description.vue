<template>
  <section id="about">
    <AnimateOnVisible name="fadeDown" :duration="1">
      <Title 
        :title="content?.object?.metadata?.title || 'Sobre mi'" 
        :description="content?.object?.metadata?.description || '-----------'" 
      />
    </AnimateOnVisible>

    <AnimateOnVisible name="fadeRight" :duration="1">
      <div class="section-content">
        <div class="container-fluid">
          <div class="row justify-content-center">
            <Photo :user="user" />
          </div>
          <div class="row">
            <div class="col-md-7 mr-auto card-mobile">
              <Presentation :content="content" />
            </div>
            <div class="col-md-4 card-mobile">
              <PersonnalCard :user="user" :links="links" />
            </div>
          </div>
        </div>
      </div>
    </AnimateOnVisible>
  </section>
</template>

<script>
import Title from './Title.vue'
import PersonnalCard from './PersonnalCard.vue'
import Presentation from './Presentation.vue'
import Photo from './Photo.vue'

export default {
  name: 'AboutMe',
  props: {
    user: {
      type: Object,
      default: () => ({
        name: 'John Doe',
        email: 'johndoe@example.com',
        phone: '+123 456 789',
        city: 'Barcelona',
        lang: 'Spanish, English',
        photo: 'https://via.placeholder.com/150'
      })
    },
    content: {
      type: Object,
      default: () => ({
        object: {
          metadata: {
            title: 'About Me (Default)',
            description: 'This is a default description text because Cosmic did not provide data.',
            pres_title: 'Presentation',
            pres_first: 'Hi! I am John Doe, a passionate developer.',
            pres_second: 'I love working with Vue, Node.js and building amazing applications.'
          }
        }
      })
    },
    links: {
      type: Object,
      default: () => ({
        facebook: 'https://facebook.com/default',
        instagram: 'https://instagram.com/default',
        linkedin: 'https://linkedin.com/in/default',
        github: 'https://github.com/default'
      })
    }
  },
  components: {
    Title,
    PersonnalCard,
    Presentation,
    Photo
  }
}
</script>

<style scoped lang="scss">
@import '@/styles/constants.scss';

#about {
  background-color: lighten(map-get($colors, dark), 100%);
}

@media (min-width: #{map-get($breakpoints, medium)}) {
  .section-content {
    width: 80%;
    margin: 0 auto;
  }
}

@media (max-width: #{map-get($breakpoints, medium)}) {
  .card-mobile {
    text-align: center !important;
    margin-top: 20px;
  }
}
</style>
