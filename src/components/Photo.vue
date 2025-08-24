<template>
  <div>
    <div class="photo">
      <a>
        <img :src="getImgUrl(user.photo)" alt="photo" />
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "Photo",
  props: {
    user: {
      type: Object,
      default: () => ({
        name: "John Doe",
        email: "johndoe@example.com",
        phone: "+123 456 789",
        city: "Barcelona",
        lang: "Spanish, English",
        photo: "default.jpg" // nombre de la foto por defecto en src/assets/img
      })
    }
  },
  methods: {
    getImgUrl(img) {
      // Si no hay imagen, usa la imagen por defecto
      const defaultImg = require("../assets/img/photo.jpg");
      if (!img || img === "") return defaultImg;

      // Si es URL de Cosmic, devuelve la URL directamente
      if (/^https:\/\/cdn\.cosmicjs\.com\/.+\.(jpg|png|gif)$/.test(img)) return img;

      // Si es nombre de archivo local en src/assets/img
      try {
        return require("../assets/img/" + img);
      } catch (err) {
        return defaultImg; // fallback si no existe el archivo
      }
    }
  }
};
</script>

<style scoped lang="scss">
.photo {
  a:focus {
    outline: none;
  }
  img {
    width: 200px;
    height: 200px;
    border-radius: 50%;
    display: inline-block;
    object-fit: cover;
  }
}
img {
  max-width: 100%;
}
</style>
