<template>
  <div>
    <div>
      <notifications group="form-feedback"></notifications>
    </div>
    <Loading v-if="isLoading" message="Sending message"/>
    <Section color="ligth" :sectionHeader="sectionHeader">
      <div slot="body" class="section-body">
        <div class="container">
          <FormContact @submitForm="onSubmit" />
        </div>
      </div>
    </Section>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'

// Components
import Section from '@/components/UI/Section'
import FormContact from '@/components/Application/FormContact'
import Loading from '@/components/UI/Loading'

export default {
  name: 'page-contact',
  middleware: ['menu', 'check-auth'],
  head: {
    title: 'Contato: André Brandão'
  },
  components: {
    Section,
    FormContact,
    Loading
  },
  data() {
    return {
      sectionHeader: {
        title: 'Contato',
        subtitle: 'Entre em contato comigo através do formulário abaixo.',
        animation: 'fadeInRight',
        icon: 'ion-md-mail'
      }
    }
  },
  computed: {
    ...mapGetters(['isLoading'])
  },
  mounted() {
    this.$store.dispatch('countPageView', 'contact')
  },
  methods: {
    onSubmit(success) {
      this.$notify({
        group: 'form-feedback',
        type: success ? 'success' : 'warn',
        title: success ? 'Mensagem enviada' : 'Mensagem não enviada',
        text: success ? 'Obrigado pelo contato, logo retornarei' : 'Tente mais tarde'
      });
    }
  }
}
</script>
