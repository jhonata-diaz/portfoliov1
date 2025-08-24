<template>
  <div>
    <h3>{{ userToShow.name }}</h3>
    <div class="data"><strong>E-mail:</strong> {{ userToShow.email }}</div>
    <div class="data"><strong>Phone:</strong> {{ userToShow.phone }}</div>
    <div class="data"><strong>City:</strong> {{ userToShow.city }}</div>
    <div class="data"><strong>Languages:</strong> {{ userToShow.lang }}</div>
    <SocialBar :links="linksToShow"/>
  </div>
</template>

<script>
import SocialBar from './SocialBar.vue'

export default {
  name: 'PersonnalCard',
  props: {
    user: {
      type: Object,
      default: () => null
    },
    links: {
      type: Object,
      default: () => null
    }
  },
  components: { SocialBar },
  computed: {
    defaultUser() {
      return {
        name: "Jhonatan Gustavo Diaz Choque",
        email: "jhon0502dc@gmail.com",
        phone: "+34 601579928",
        city: "Barcelona",
        lang: "English, Spanish, Catalan"
      }
    },
    userToShow() {
      const u = this.user?.object?.metadata ?? {};
      return {
        name: u.name || this.defaultUser.name,
        email: u.email || this.defaultUser.email,
        phone: u.phone || this.defaultUser.phone,
        city: u.city || this.defaultUser.city,
        lang: u.lang || this.defaultUser.lang
      };
    },
    defaultLinks() {
      return {
        facebook: "https://facebook.com/example",
        instagram: "https://instagram.com/example",
        linkedin: "https://linkedin.com/in/example",
        github: "https://github.com/example"
      };
    },
    linksToShow() {
      const l = this.links?.object?.metadata ?? {};
      return {
        facebook: l.facebook || this.defaultLinks.facebook,
        instagram: l.instagram || this.defaultLinks.instagram,
        linkedin: l.linkedin || this.defaultLinks.linkedin,
        github: l.github || this.defaultLinks.github
      };
    }
  }
}
</script>

<style scoped lang="scss">
@import '@/styles/constants.scss';

.data {
  margin-bottom: 15px;
}
</style>
