<template>
  <div class="player-card">
    <div
      class="picture"
      v-lazy:background-image="'/images/players/background_player.jpg'"
    >
      <img v-lazy="picture" :alt="fullname" />
    </div>
    <div class="body">
      <label>Nom / Pseudo</label>
      <div class="fullname">{{ fullname }}</div>
      <h2>{{ player.nickname }}</h2>
      <label>Rôle</label>
      <p class="role">{{ player.role }}</p>
      <div class="socials" v-if="player.socials.length > 0">
        <a
          v-for="social in player.socials"
          :key="social.type"
          :href="social.url"
          target="_blank"
          rel="nofollow"
          :aria-label="`${social.type} pour ${fullname}`"
        ><i :class="'icon-' + social.type"></i></a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ['player'],

  computed: {
    fullname () {
      return `${this.player.firstname || ''} ${this.player.lastname || ''}`.trim()
    },

    picture () {
      if (this.player.picture) {
        return this.player.picture
      }

      return '/images/players/default.png'
    }
  },
}
</script>
