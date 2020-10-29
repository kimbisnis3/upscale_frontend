<template>
  <div class="home">
    <template>
      <div class="container">
        <table class="table">
          <thead>
            <th>ID</th>
            <th>Name</th>
            <th>Username</th>
            <th>Email</th>
            <th>Phone</th>
            <th>Website</th>
            <th>Action</th>
          </thead>
          <tbody>
            <tr v-for="item in result" :key="item.id">
              <td>{{item.id}}</td>
              <td>{{item.name}}</td>
              <td>{{item.username}}</td>
              <td>{{item.email}}</td>
              <td>{{item.phone}}</td>
              <td>{{item.website}}</td>
              <td><router-link :to="'/home/' + item.id"><button class="btn btn-md btn-primary">Detail</button> </router-link></td>
            </tr>
          </tbody>
        </table>
      </div>
    </template>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data: () => ({
    result: null,
    initlimit: 10,
    plus : 10,
  }),
  methods: {
    getdata() {
      const baseURI = `http://localhost:8000/userall`;
      this.$axios.get(baseURI).then((result) => {
        this.result = result.data;
      });
    },
  },
  mounted() {
    this.getdata();
  },
}
</script>
