<template>
  <div>
    <v-row>
      <v-col
        cols="4"
        v-for="(user, index) in users"
        :key="index"
      >
        <v-card 
          class="mx-auto mr-5"
          outlined
          color="green"
          dark
        >
          <v-list-item three-line>
            <v-list-item-avatar
              tile
              size="80"
              color="grey"
            >
              <img src="https://randomuser.me/api/portraits/men/7.jpg" style="max-width: 100%">
            </v-list-item-avatar>

            <v-list-item-content>
              <v-list-item-title class="headline mb-1">{{ user.name }}</v-list-item-title>
              <v-list-item-subtitle>{{ user.username }}</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>

          <v-card-actions>
            <router-link 
              :to="'users/' + user.id"
              
            >
              Перейти в профиль
            </router-link>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
    
  </div>
</template>

<script>
export default {
  name: 'Users',
  components: {
  },
  data() {
    return {
      users: {},
    };
  },
  methods: {
    loadUsersInfo() {
      this.axios
        .get("http://jsonplaceholder.typicode.com/users")
          .then( (response) => {
              this.users = response.data;
              console.log(this.users);
            }
          );
    }
  },
  mounted() {
    this.loadUsersInfo();
  },
  watch: {
    $route() {
      this.loadUsersInfo();
    }
  }
}
</script>
