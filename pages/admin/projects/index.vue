<template>
  <Section color="success" :sectionHeader="sectionHeader">
    <div slot="body" class="section-body">
      <div class="container">

        <div class="t-center">
          <nuxt-link to="/admin/projects/create" class="btn btn-primary" title="Novo Projeto">
            Novo Projeto
          </nuxt-link>
        </div>

        <div class="t-center" v-if="!activedProjects.length">
          <p class="t-primary">Nenhum projeto cadastrado ainda</p>
        </div>

        <div class="table-responsive" v-if="activedProjects.length">
          <table class="table">
            <thead class="table-header">
              <tr>
                <th>#</th>
                <th>Atalho</th>
                <th>Nome</th>
                <th>Empresa</th>
                <th>Editar</th>
              </tr>
            </thead>
            <tbody class="table-body">
              <tr v-for="(project, index) in activedProjects">
                <td>{{ project.id }}</td>
                <td>{{ project.slug }}</td>
                <td>{{ project.title }}</td>
                <td>{{ project.company }}</td>
                <td class="has-button">
                  <nuxt-link class="tag tag-success" :to="`/admin/projects/${ project.id }`" :name="`Remover ${ project.title }`">
                    <i class="ion ion-md-create"></i>
                    <span class="sr-only">Editar</span>
                  </nuxt-link>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </Section>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'

// Components
import Section from '@/components/UI/Section'

export default {
  name: 'page-admin-projects-index',
  layout: 'admin',
  middleware: ['menu', 'check-auth', 'auth'],
  components: {
    Section
  },
  data () {
    return {
      sectionHeader: {
        title: 'Projetos',
        subtitle: 'Lista de projetos adicionados, é possível adicionar, editar e remove-los',
        animation: 'fadeInLeft',
        icon: 'ion-md-code-working'
      }
    }
  },
  computed: {
    ...mapGetters(['activedProjects'])
  }
}
</script>

<style scoped lang="stylus">
  .table-responsive,
  .t-primary
    margin-top 50px

  .t-primary
    font-weight 300
    font-size 2rem

  .tag
    i
      margin 0
</style>
