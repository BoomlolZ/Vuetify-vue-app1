<template>
  <v-app>
    <v-container>
      <div class="d-flex justify-center">
        <h1>Welcome to Data-Table</h1>
      </div>
      <AddBtn @save="saveUser" />
      <v-simple-table>
        <template>
          <thead class="orange lighten-2">
            <tr>
              <th class="text-center"><h2>First-Name</h2></th>
              <th class="text-center"><h2>Last-Name</h2></th>
              <th class="text-center"><h2>User-Name</h2></th>
              <th class="text-center"><h2>Avatar</h2></th>
              <th class="text-center"><h2>Edit</h2></th>
              <th class="text-center"><h2>Delete</h2></th>
            </tr>
          </thead>
          <tbody class="orange lighten-5 text-center">
            <tr v-for="user in users" :key="user.id">
              <td>{{ user.fname }}</td>
              <td>{{ user.lname }}</td>
              <td>{{ user.username }}</td>
              <td>
                <v-avatar size="50px"><img :src="user.avatar" /></v-avatar>
              </td>
              <td>
                <EditBtn
                  :id="user.id"
                  :fname="user.fname"
                  :lname="user.lname"
                  :username="user.username"
                  :email="user.email"
                  :avatar="user.avatar"
                  @edit="EditUser"
                />
              </td>
              <td><DeleteBtn :id="user.id" @del="delUser" /></td>
            </tr>
          </tbody>
        </template>
      </v-simple-table>
    </v-container>
  </v-app>
</template>

<script>
import axios from "axios";
import AddBtn from "./components/AddBtn.vue";
import DeleteBtn from "./components/DeleteBtn.vue";
import EditBtn from "./components/EditBtn.vue";
export default {
  name: "App",
  components: {
    AddBtn,
    DeleteBtn,
    EditBtn,
  },
  data() {
    return {
      users: [],
    };
  },

  mounted() {
    this.getData();
  },
  methods: {
    async saveUser(value) {
      const user = await axios.post(
        "https://www.mecallapi.com/api/users/create",
        value
      );
      if (user.status == "200") {
        this.getData();
      } else {
        console.log(value);
      }
    },
    async delUser(value) {
      console.log(value);
      const user = await axios.delete(
        "https://www.mecallapi.com/api/users/delete",
        { data: { id: value.id } }
      );

      if (user.status == "200") {
        this.getData();
      }
    },
    async EditUser(value) {
      console.log(value);
      const user = await axios.put(
        "https://www.mecallapi.com/api/users/update",
        {
          id: value.id,
          fname: value.p_fname,
          lname: value.p_lname,
          username: value.p_username,
          email: value.p_email,
          avatar: value.p_avatar,
        }
      );

      if (user.status == "200") {
        this.getData();
      }
    },
    async getData() {
      const users = await axios.get("https://www.mecallapi.com/api/users");
      if (users.status == "200") {
        this.users = users.data;
        console.log(this.users);
      } else {
        console.log(users);
      }
    },
  },
};
</script>
