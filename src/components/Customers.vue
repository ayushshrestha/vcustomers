<template>
  <div class="customers container">
    <h1 class="page-header ">Manage Customers</h1>
    <table class="table table-striped">
      <thead>
        <tr>
          <th>First Name</th>
          <th>Last Name</th>
          <th>Email</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="customer in customers">
          <td v-text="customer.first_name"></td>
          <td v-text="customer.last_name"></td>
          <td v-text="customer.email"></td>
          <td></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'customers',
  data () {
    return {
      customers: []
    }
  },
  methods: {
    fetchCustomers(){
      this.$http.get('http://slimapp/api/customers')
      .then(function(response){
        this.customers = response.body;
      });
    }
  },
  created: function(){
    this.fetchCustomers();
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
