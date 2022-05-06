<template>
  <v-dialog v-model="dialog" persistent max-width="400">
    <template v-slot:activator="{ on, attrs }">
      <v-btn class="mt-2 mb-3" color="error" v-bind="attrs" v-on="on">
        <v-icon>mdi-delete</v-icon>
      </v-btn>
    </template>
    <v-card>
      <v-card-title class="text-h5">
        Are you sure to Delete this Data?
      </v-card-title>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn color="green darken-1" text @click="dialog = false"> No </v-btn>
        <v-btn
          color="green darken-1"
          text
          @click="$emit('del',{id}); dialog = false">
          Yes
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>
<script>

export default {
  name: "DeleteBtn",
  props: {
    id: Number,
  },
  data() {
    return {
      dialog: false,
    };
  },
  methods: {
   
  },
};
</script>
