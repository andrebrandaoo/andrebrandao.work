<template>
  <nav class="app-nav">
    <ul class="app-nav-list start mobile">
      <li class="app-nav-item">
        <button type="button" class="app-nav-link active" name="button" @click="toggleMenu(!menuIsClosed)">
          <i class="ion f-1-5" :class="menuIsClosed ? 'ion-md-close' : 'ion-md-menu'"></i>
          <span class="sr-only">{{ menuIsClosed ? 'Close Menu' : 'Open Menu' }}</span>
        </button>
      </li>
      <li class="app-nav-item">
        <span class="app-nav-link active" title="André Brandão">André Brandão</span>
      </li>
    </ul>

    <ul class="app-nav-list start side" :class="{ 'is-opened': menuIsClosed }">
      <li class="app-nav-item">
        <nuxt-link class="app-nav-link" exact to="/" title="Início">Início</nuxt-link>
      </li>
      <li class="app-nav-item">
        <nuxt-link class="app-nav-link" exact to="/sobre" title="Sobre">Sobre</nuxt-link>
      </li>
      <li class="app-nav-item">
        <nuxt-link class="app-nav-link" to="/projetos" title="Projetos">Projetos</nuxt-link>
      </li>
      <li class="app-nav-item">
        <nuxt-link class="app-nav-link" exact to="/artigos" title="Artigos">Artigos</nuxt-link>
      </li>
      <li class="app-nav-item">
        <nuxt-link class="app-nav-link" exact to="/contato" title="Contato">Contato</nuxt-link>
      </li>
    </ul>

    <ul class="app-nav-list end">
      <li class="app-nav-item">
        <a class="app-nav-link github" href="https://github.com/andrebrandaoo" title="Github">
          <i class="ion ion-logo-github f-1-5"></i>
          <span class="sr-only">Github</span>
        </a>
      </li>
      <li class="app-nav-item" v-if="isAuthenticated">
        <nuxt-link class="app-nav-link github" to="/admin" title="admin">
          <i class="ion ion-md-apps f-1-5"></i>
          <span class="sr-only">Admin</span>
        </nuxt-link>
      </li>
    </ul>
  </nav>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'

export default {
  name: 'component-application-header',
  computed: {
    ...mapGetters(['menuIsClosed', 'isAuthenticated'])
  },
  methods: {
    ...mapActions(['toggleMenu'])
  },
}
</script>

<style scoped lang="stylus">
</style>
