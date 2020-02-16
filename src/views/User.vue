<template>
  <div>
    <v-row class="text-left">
      <v-col cols="10">
        <h1 class="green--text text--darken-2">
          <v-icon large color="green darken-2">mdi-account-outline</v-icon>
          {{ user.name }}
        </h1>
      </v-col>
    </v-row>
    <v-row class="text-left">
      <v-col cols="2">
        <img src="https://randomuser.me/api/portraits/men/7.jpg" style="max-width: 100%">
      </v-col>
      <v-col cols="10" class="text-left">
        <p>
          Веб-сайт: <a :href="user.website" target="_blank">{{ user.website }}</a>
        </p>
        <p>
          E-mail: <a href="user.email">{{ user.email }}</a>
        </p>
        <p>
          Город: {{ user.address.city }}
        </p>
        <p>
          Место работы: {{ user.company.name }}
        </p>
      </v-col>
    </v-row>

    <v-divider class="my-3"/>

    <h2>
      Публикации
    </h2>

    <v-card
      class="mt-5 mr-10"
      color="green"
      dark
    >
      <v-card-title>
        <v-list-item-avatar>
          <v-img
            src="https://randomuser.me/api/portraits/men/7.jpg"
          />
        </v-list-item-avatar>
        <v-list-item-content>
          <v-list-item-title>Иванов Иван</v-list-item-title>
        </v-list-item-content>
      </v-card-title>

      <v-card-text
        align-center
        justify-center
      >
        Дарова, я зарегался)
      </v-card-text>

      <v-card-actions>
        <v-list-item class="grow">
          <v-row
            align="center"
            justify="end"
          >
            <v-icon class="mr-1">mdi-heart</v-icon>
            <span class="subheading mr-2">0</span>
            <span class="mr-1">·</span>
            <v-icon class="mr-1">mdi-share-variant</v-icon>
            <span class="subheading">0</span>
          </v-row>
        </v-list-item>
      </v-card-actions>
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
      user: {},
    };
  },
  methods: {
    loadUserInfo() {
      this.axios
      .get("http://188.225.47.187/api/jsonstorage/9bf50d32cf12ed281dd4244b890bd58a")
        .then( (response) => {
          this.users = response.data;
          console.log(this.user);
        }
    );
    }
  },
  mounted() {
    this.loadUserInfo();
  },
  watch: {
    $route() {
      this.loadUserInfo();
    }
  }
}
</script>
