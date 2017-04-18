<template>
  <q-layout>
    <div slot="header" class="toolbar">
      <button class="hide-on-drawer-visible" @click="$refs.leftDrawer.open()"> <i>menu</i></button>
      <q-toolbar-title :padding="1"> Github Explorer </q-toolbar-title>      
    </div>

    <q-drawer ref="leftDrawer">
       <div class="toolbar">
          <q-toolbar-title> Menu </q-toolbar-title>
      </div>
      <div class="list no-border platform-delimiter">
         <div class="list-label">Meu Perfil </div>
          <q-drawer-link icon="mail" to="/account">Account</q-drawer-link>
          <q-drawer-link icon="alarm" to="/alarms">Alarms</q-drawer-link>
        </div>
    </q-drawer>

    <div class="layout-view">
        <div class="list">
             <div class="item multiple-lines">
                <i class="item-primary">edit</i>
                <div class="item-content">
                    <div class="floating-label">
                        <input required class="full-width" v-model="username">
                        <label>Nome de Usuário</label>
                    </div>
                </div>
            </div>

            
            <div class="item multiple-lines">
                <i class="item-primary">lock </i>
                <div class="item-content">
                    <div class="floating-label">
                        <input type="password" required class="full-width" v-model="password">
                        <label>Senha</label>
                    </div>
                </div>
            </div>
        </div>
        <br>
        <button class="primary small" @click="validar()"> Entrar </button>
    </div>
  </q-layout>
</template>

<script>
  import { Toast } from 'quasar'
  import { Loading } from 'quasar'

  export default {
    data () {
      return {
        username: '',
        password: ''
      }
    },
    methods: {
      validar () {
        if(this.username == 'Leonardo' & this.password == 'Pereira')
          Toast.create.positive('Bem-vindo')
        else
          Toast.create.negative('Inválido')
      }
    },
    beforeCreate: () => {
      Loading.show({
        message: 'Carregando aplicação'        
      })

      setTimeout(()=>{Loading.hide()} , 5000)
    }
  }
</script>

<style lang="styl">

</style>
