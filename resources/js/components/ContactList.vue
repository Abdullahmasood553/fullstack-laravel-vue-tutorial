<template>
    <div class="container">
          <h2 class="text-center p-2 text-white bg-primary mt-5">Contacts</h2>

          <table class="table">
              <thead>
                  <tr>
                    <th scope="col">#</th>
                    <th scope="col">Name</th>
                    <th scope="col">Email</th>
                    <th scope="col">Designation</th>
                    <th scope="col">Contact Number</th>
                    <th class="col">Action</th>
                  </tr>
              </thead>


              <tbody v-for="contact in contacts" :key="contact.id">
                  <tr>
                    <th scope="row">{{ contact.id }}</th>
                    <td>{{ contact.name }}</td>
                    <td>{{ contact.email }}</td>
                    <td>{{ contact.designation }}</td>
                    <td>{{ contact.contact_no }}</td>
                    <td><button class="btn btn-danger btn-sm">Delete</button></td>
                  </tr>
              </tbody>
          </table>
    </div>
</template>

<script>
export default {
    name: 'Contact',
    created() {
        this.loadData();
    },
    methods: {
        loadData() {
            let url = this.url + '/api/getContacts';
            this.axios.get(url).then(response => {
                this.contacts = response.data
                console.log(this.contacts);
            });
        }
        },
        mounted() {
            console.log('Contact List Component Mounted');
        },
        data() {
            return {
                url: document.head.querySelector('meta[name="url"]').content,
                contacts:[]
            }
        }
}
</script>

