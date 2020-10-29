<template>
  <div class="container">
    <h1>Detail</h1>
    <table class="table">
      <tbody>
        <tr>
          <td>ID</td>
          <td>{{ result.id }}</td>
        </tr>
        <tr>
          <td>Name</td>
          <td>{{ result.name }}</td>
        </tr>
        <tr>
          <td>Username</td>
          <td>{{ result.username }}</td>
        </tr>
        <tr>
          <td>Email</td>
          <td>{{ result.email }}</td>
        </tr>
        <tr>
          <td>Phone</td>
          <td>{{ result.phone }}</td>
        </tr>
        <tr>
          <td>Website</td>
          <td>{{ result.website }}</td>
        </tr>
      </tbody>
    </table>
    <h5><router-link to="/home">Back to Home</router-link></h5>
  </div>
</template>

<script>
export default {
  name: "Homedet",
  data: () => ({
    result: {},
  }),
  methods: {
    getdata() {
      const baseURI = `http://localhost:8000/user/${this.$route.params.id}`;
      this.$axios.get(baseURI).then((result) => {
        this.result = result.data;
      });
    },
  },
  mounted() {
    this.getdata();
  },
};
</script>
