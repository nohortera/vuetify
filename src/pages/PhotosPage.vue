<template>
  <v-container>
    <PhotoForm @addPhoto="addPhoto"/>
    <v-row>
      <PhotoCard
          v-for="photo in $store.getters.getAllPhotos"
          :key="photo.id"
          :photo="photo"
      />
<!--      <PhotoCard-->
<!--          @openPhoto="openPhoto"-->
<!--          v-for="photo in $store.getters.getAllPhotos"-->
<!--          :key="photo.id"-->
<!--          :photo="photo"-->
<!--      />-->
    </v-row>
    <PhotoDialog
        :photo="currentPhoto"
    />
<!--    <PhotoDialog-->
<!--        :photo="currentPhoto"-->
<!--        v-model="dialogVisible"-->
<!--    />-->
  </v-container>
</template>

<script>
import PhotoCard from "@/components/photo/PhotoCard";
import PhotoForm from "@/components/photo/PhotoForm";
import PhotoDialog from "@/components/photo/PhotoDialog";
export default {
  components: {PhotoDialog, PhotoForm, PhotoCard},
  data: () => ({
    photos: [],
    currentPhoto: {},
    dialogVisible: false
  }),
  mounted() {
    // this.fetchPhotos()
    this.$store.dispatch('fetchPhotos')
  },
  methods: {
    // fetchPhotos() {
    //   this.axios.get('https://jsonplaceholder.typicode.com/photos?_limit=10')
    //       .then(response => this.photos = response.data)
    // },
    addPhoto(photo) {
      this.photos.push(photo)
    },
    // openPhoto(photo) {
    //   this.currentPhoto = photo
    //   this.dialogVisible = true
    // }
  }
}
</script>

<style scoped>

</style>
