<template>
  <v-dialog
      v-model="$store.getters.getDialogVisible"
      max-width="600"
      @click:outside="$store.commit('hideDialog')"
  >
<!--  <v-dialog-->
<!--      v-model="dialogVisible"-->
<!--      max-width="600"-->
<!--  >-->
    <v-card>
      <v-card-title>{{ full_title }}</v-card-title>
      <v-card-text>
        <v-img
            :src="$store.getters.getCurrentPhoto.url"
        />
<!--        <v-img-->
<!--          :src="photo.url"-->
<!--        />-->
      </v-card-text>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  props: {
    photo: {
      type: Object,
      required: true
    },
    // value: {
    //   type: Boolean,
    //   default: false
    // }
  },
  // created() {
  //   this.dialogVisible = this.value
  // },
  // data: () => ({
  //   dialogVisible: false
  // }),
  // watch: {
  //   value(newValue) {
  //     this.dialogVisible = newValue
  //   },
  //   dialogVisible(newValue) {
  //     this.$emit('input', newValue)
  //   }
  // },
  computed: {
    full_title() {
      return `Photo title - ${this.$store.getters.getCurrentPhoto.title}`
    }
    // full_title() {
    //   return `Photo title - ${this.photo.title}`
    // }
  }
}
</script>

<style scoped>

</style>
