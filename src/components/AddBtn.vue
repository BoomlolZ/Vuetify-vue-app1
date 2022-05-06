<template>
  <v-container>
  <template>
    <v-dialog width="600px"
      v-model="dialog"
      hide-overlay
      transition="dialog-bottom-transition"
      
    >
      <template v-slot:activator="{ on, attrs }">
        <v-col class="d-flex justify-end">
          <v-btn color="primary"
          dark v-bind="attrs" v-on="on">
          Add Data</v-btn>
        </v-col>
      </template>
        <v-card>
        <v-toolbar
          dark
          color="primary"
        >
        
          <v-btn
            icon
            dark
            @click="dialog = false"
          >
          <v-icon>mdi-close</v-icon>
          </v-btn>
          
          <v-toolbar-title>Add some new data</v-toolbar-title>
           <v-spacer></v-spacer>
          <button @click="$emit('save',saveData());clear(),dialog = false">save</button>
        </v-toolbar>
              <v-form class="px-3">
                  <v-text-field label="Full-name" v-model="fname"></v-text-field>
                  <v-text-field label="last-name" v-model="lname"></v-text-field>
                  <v-text-field label="ีuser-name" v-model="username"></v-text-field>
                  <v-text-field label="Email" v-model="email"></v-text-field>
                  <v-text-field label="Avatar" v-model="avatar"></v-text-field>
              </v-form>
        <v-divider></v-divider>
      </v-card>
    </v-dialog>
  </template>
  </v-container>
</template>
<script>
export default {
  name: "AddBtn",
  data() {
    return {
      dialog: false,
      fname: "",
      lname: "",
      username: "",
      email: "",
      avatar: "",
    };
  },
  methods: {
    saveData() {
      const data = {
        fname: this.fname,
        lname: this.lname,
        username: this.username,
        email: this.email,
        avatar: this.avatar,
      };
      return data;
    },
    clear() {
      this.fname = "";
      this.lname = "";
      this.username = "";
      this.email = "";
      this.avatar = "";
    },
  },
};
</script>
