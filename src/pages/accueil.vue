<template>
  <div id="main">
    <div class="center mt-15">
        <v-card>
          <v-img
          src="/banderole.png">
          </v-img>
        </v-card>
    </div>


  </div>
</template>

<script>

export default {
  name: "accueil",
  methods: {

    /**
     * changes, redirects to the page
     * @param to :  name of the page to redirect
     */
    redirect(to){
      this.$router.push(to)
    },

  }
}
</script>

<style>
</style>


