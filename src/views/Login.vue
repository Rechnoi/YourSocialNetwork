<template>
  <div class="d-flex justify-center">
        <v-card width="600px" class="mt-12 pa-10">
            <v-card-title>
                Войдите в аккаунт
            </v-card-title>

            <v-text-field
                label="Введите логин"
                v-model="login"
                outlined
            ></v-text-field>

            <v-text-field
                label="Введите пароль"
                v-model="password"
                outlined
            ></v-text-field>

            <v-btn @click="authenticate">
                Войти
            </v-btn>
        </v-card>
    </div>
</template>

<script>
export default {
  name: 'User',
  components: {
  },
  data() {
    return {
      login: '',
      password: ''
    };
  },
  methods: {
    authenticate() {
      this.axios
      .get("http://188.225.47.187/api/jsonstorage/9bf50d32cf12ed281dd4244b890bd58a")
        .then( (response) => {
          let users = response.data;
          let found = false;
          for (let user of users) {
            if (this.login == user.login && this.password == user.password) {
              this.$router.push('/users/' + user.id);
              found = true;
              break;
            }
          }
          if (!found)
            window.alert('ERROR! Неверный логин иили пароль!');
        }
    );
    }
  }
}
</script>
