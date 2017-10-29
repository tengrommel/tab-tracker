<template>
<v-layout>
  <panel title="Song Metadata">
    <div>
      {{song.title}}
      {{song.artist}}
      {{song.genre}}
      {{song.albumImageUrl}}
    </div>
    <img class="album-image" :src="song.albumImageUrl">
  </panel>
</v-layout>
</template>

<script>
import SongsService from '@/services/SongsService'
import Panel from '@/components/Panel'

export default {
  data () {
    return {
      song: {}
    }
  },
  async mounted () {
    const songId = this.$store.state.route.params.songId
    this.song = (await SongsService.show(songId)).data
  },
  components: {
    Panel
  }
}
</script>

<style scoped>

</style>
