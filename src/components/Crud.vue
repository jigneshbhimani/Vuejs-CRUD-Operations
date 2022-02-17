<template>
  <div class="container">
    <h2 class="text-center-1 mt-5"><b>CRUD Operation</b></h2>
    <br />

    <div class="d-flex">
      <input
        v-model="user"
        type="text"
        class="text-center"
        placeholder="Enter User"
      />
      <button @click="addUser" class="btn btn-info">Add</button>
    </div>
    <br />

    <table class="table table-bordered mt-2">
      <thead>
        <tr class="raw">
          <th scope="col" class="text-center">User</th>
          <th scope="col" class="text-center">Edit</th>
          <th scope="col" class="text-center">Delete</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(user, index) in users" :key="index">
          <th>
            <span class="text-center">{{ user.name }}</span>
          </th>
          <td>
            <div class="text-center" @click="updateUser(index)">
              <span class="Update">Update</span>
            </div>
          </td>
          <td>
            <div class="text-center" @click="deleteUser(index)">
              <span class="Delete">Delete</span>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
    <br />
  </div>
</template>

<script>
export default {
  props: {
    msg: String,
  },
  data() {
    return {
      user: "",
      editedUser: null,
      users: [
        {
          name: "Rohit",
        },
        {
          name: "Sachin",
        },
        {
          name: "Virat",
        },
        {
          name: "Kapil",
        },
      ],
    };
  },
  methods: {
    addUser() {
      if (this.user.length === 0) return;

      if (this.editedUser === null) {
        this.users.push({
          name: this.user,
        });
      } else {
        this.users[this.editedUser].name = this.user;
        this.editedUser = null;
      }
      this.user = ""; // clear the input field
    },

    deleteUser(index) {
      this.users.splice(index, 1);
    },

    updateUser(index) {
      this.user = this.users[index].name;
      this.editedUser = index;
    },
  },
};
</script>

<style scoped>
.container {
  height: auto;
  width: 40%;
}

.table {
  border-color: black;
  box-shadow: 1px 1px 3px #333333;
}

.raw {
  color: brown;
  font-weight: bold;
}

.Delete {
  color: red;
}

.Update {
  color: green;
}

.text-center {
  font-weight: bold;
}
</style>

