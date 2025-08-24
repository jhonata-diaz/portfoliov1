<template>
  <div class="social-wrap">
    <ul>
      <li>
        <a :href="linksToUse.facebook" target="_blank">
          <font-awesome-icon class="icon" :icon="['fab', 'facebook-square']" />
        </a>
      </li>
      <li>
        <a :href="linksToUse.instagram" target="_blank">
          <font-awesome-icon class="icon" :icon="['fab', 'instagram-square']" />
        </a>
      </li>
      <li>
        <a :href="linksToUse.linkedin" target="_blank">
          <font-awesome-icon class="icon" :icon="['fab', 'linkedin']" />
        </a>
      </li>
      <li>
        <a :href="linksToUse.github" target="_blank">
          <font-awesome-icon class="icon" :icon="['fab', 'github-square']" />
        </a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "SocialBar",
  props: {
    links: {
      type: Object,
      default: () => ({})
    }
  },
  computed: {
    linksToUse() {
      // Si no hay links desde props, usar defaults
      return {
        facebook: this.links?.object?.metadata?.facebook || "https://facebook.com/example",
        instagram: this.links?.object?.metadata?.instagram || "https://instagram.com/example",
        linkedin: this.links?.object?.metadata?.linkedin || "https://www.linkedin.com/in/jhonatan-gustavo-diaz-choque-b607052a9/",
        github: this.links?.object?.metadata?.github || "https://github.com/jhonata-diaz"
      };
    }
  }
};
</script>

<style scoped lang="scss">
@import "@/styles/constants.scss";

.social-wrap {
  li {
    display: inline-block;
    margin-right: 10px;
  }
  .icon {
    font-size: 3rem;
  }
}
</style>
