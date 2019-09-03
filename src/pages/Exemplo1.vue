<template>
  <q-page padding>
    <h3>Formulário</h3>

    <q-form @submit="save" @reset="reset" class="q-gutter-md">

      <q-input
        outlined
        label="Nome"
        v-model="user.name"
        color="green"
        hint="Obrigatório, precisa ter 3 ou mais caracteres!"
        :rules="[
          val => !!val || 'Campo Obrigatório',
          val => val.length > 2 || 'Nome muito curto'
        ]"
      >
        <template v-slot:prepend>
          <q-icon name="account_box"/>
        </template>
      </q-input>

      <q-input
        outlined
        label="E-mail"
        v-model="user.email"
        color="green"
        hint="Obrigatório, precisa ser um endereço de E-mail válido!"
        :rules="[
          val => !!val || 'Campo Obrigatório',
          val => /^[a-zA-Z.\-_]+@[a-zA-Z]+\.[a-z]+[a-zA-Z.]*$/.test(val) || 'E-mail inválido'
        ]"
      >
        <template v-slot:prepend>
          <q-icon name="email"/>
        </template>
      </q-input>

      <p>
        <q-toggle
          v-model="user.newsletter"
          label="Aceita receber novidades do canal?"
          color="green"
          checked-icon="check"
          unchecked-icon="clear"
        />
      </p>

      <q-btn type="submit" color="primary">Salvar</q-btn>
      <q-btn type="reset" color="secondary" class="q-ml-sm">Resetar</q-btn>
    </q-form>
  </q-page>
</template>

<script>
export default {
  name: 'Exemplo1Page',
  data () {
    return {
      user: {
        newsletter: false
      }
    }
  },
  mounted () {
    this.$q.notify.setDefaults({
      position: 'bottom-right',
      color: 'green'
    })
  },
  methods: {
    save () {
      this.$q.notify({
        message: 'Salvo com sucesso!'
      })
    },
    reset () {
      this.user = {
        newsletter: false
      }
    }
  }
}
</script>

<style>
</style>
