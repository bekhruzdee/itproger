<template>
  <input type="text" v-model="userName" placeholder="Name" />
  <input type="text" v-model="userPass" placeholder="Password" />
  <input type="text" v-model="userEmail" placeholder="Email" />
  <p className="error">{{ error }}</p>
  <button @click="sendData">Send</button>

  <div v-if="this.users.length == 0">Don't have users</div>
  <div v-else-if="this.users.length == 1">Users has 1</div>
  <div v-else className="user">Users has more than 1 element</div>

  <div v-for="(el, index) in users" :key="index" className="user">
    <h3>{{ el.name }}</h3>
    <p>
      {{ el.email }} - <b>{{ el.pass }}</b>
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: [],
      error: "",
      userName: "",
      userPass: "",
      userEmail: "",
    };
  },
  methods: {
    sendData() {
      if (this.userName == "") {
        this.error = "Name is required";
        return;
      } else if (this.userPass == "") {
        this.error = "Password is required";
        return;
      } else if (this.userEmail == "") {
        this.error = "Email is required";
        return;
      }

      this.error = "";

      this.users.push({
        name: this.userName,
        pass: this.userPass,
        email: this.userEmail,
      });
    },
  },
};
</script>

<style scoped>
input {
  display: block;
  margin-bottom: 10px;
  border-radius: 3px;
  border: 1px solid silver;
  outline: none;
  padding: 10px 15px;
}
button {
  border: 0;
  border-radius: 5px;
  outline: none;
  padding: 10px 15px;
  background: #6cd670;
  color: #167f3d;
  font-weight: bold;
  cursor: pointer;
  transition: transform 500ms ease;
}
button:hover {
  transform: translateY(-5px);
}
.user {
  width: 500px;
  margin-top: 20px;
  border: 1px solid silver;
  color: #222;
  padding: 20px;
  border-radius: 5px;
}
</style>
