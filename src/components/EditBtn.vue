<template>
  <v-dialog v-model="dialog" persistent max-width="800">
    <template v-slot:activator="{ on, attrs }">
      <v-btn class="mt-2 mb-3" color="success" dark v-bind="attrs" v-on="on">
        <v-icon>mdi-pencil</v-icon>
      </v-btn>
    </template>
    <v-card>
      <v-card-title class="text-h5">Update some new Data? </v-card-title>
      <v-card-text>
        <v-form class="px-3">
          <v-text-field
            v-model="p_fname"
            label="First-Name"
            prepend-icon="mdi-account"
          ></v-text-field>
          <v-text-field
            v-model="p_lname"
            label="Last-Name"
            prepend-icon="mdi-account"
          ></v-text-field>
          <v-text-field
            v-model="p_username"
            label="User-Name"
            prepend-icon="mdi-account"
          ></v-text-field>
          <v-text-field
            v-model="p_email"
            label="E-mail"
            prepend-icon="mdi-email"
          ></v-text-field>
          <v-text-field
            v-model="p_avatar"
            label="Avatar"
            prepend-icon="mdi-emoticon-cool"
          ></v-text-field>
        </v-form>
      </v-card-text>

      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn color="green darken-1" text @click="dialog = false">
          Cancel
        </v-btn>
        <v-btn
          color="green darken-1"
          text
          @click="
            $emit('edit', {
              id,
              p_fname,
              p_lname,
              p_username,
              p_email,
              p_avatar,
            });
            dialog = false;
          "
        >
          Save
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>
<script>
// import axios from 'axios'
// const dataUrl = "http://localhost:3000/database"

export default {
  name: "EditBtn",
  props: {
    id: Number,
    fname: String,
    lname: String,
    username: String,
    email: String,
    avatar: String,
  },
  data() {
    return {
      p_fname: this.fname,
      p_lname: this.lname,
      p_username: this.username,
      p_email: this.email,
      p_avatar: this.avatar,
      dialog: false,
    };
  },

  methods: {},
};
</script>
