<template>
  <div>
    <div class="container mt-3">
      <div class="row">
        <div class="col">
          <p class="h3 text-success fw-bold">Edit Contact</p>
          <p class="fst-itailic">Lorem ipsum dolor sit amet consectetur adipisicing elit. Velit hic quibusdam, obcaecati aliquid veritatis officiis sint exercitationem voluptatem aut eveniet, assumenda magni, blanditiis expedita pariatur maiores fugiat ex excepturi nam.</p>
        </div>
      </div>
    </div>
    <div class="container mt-3">
      <div class="row">
        <div class="col-md-3">
          <form @submit.prevent="updateSubmit">
            <div class="mb-2">
              <input v-model="contact.name" type="text" class="form-control" placeholder="Name">
            </div>
            <div class="mb-2">
              <input v-model="contact.photo" type="text" class="form-control" placeholder="Photo URL">
            </div>
            <div class="mb-2">
              <input v-model="contact.email" type="text" class="form-control" placeholder="Email">
            </div>
            <div class="mb-2">
              <input v-model="contact.mobile" type="number" class="form-control" placeholder="Mobile">
            </div>
            <div class="mb-2">
              <input v-model="contact.company" type="text" class="form-control" placeholder="Company">
            </div>
            <div class="mb-2">
              <input v-model="contact.title" type="text" class="form-control" placeholder="Title">
            </div>
            <div class="mb-2">
              <select v-model="contact.groupId" class="form-control" v-if="groups.length > 0">
                <option value="">Select Group</option>
                <option :value="group.id" v-for="group of groups" :key="group.id">{{group.name}}</option>
              </select>
            </div>
            <div class="mb-2">
              <input type="submit" class="btn btn-success" value="Update">
            </div>
          </form>
        </div>
        <div class="col-md-4">
          <img :src="contact.photo" alt="" class="contact-img"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ContactService } from '@/services/ContactService'

export default {
  name: "EditContact",
  data : function () {
    return {
      contactId : this.$route.params.contactId,
      loading : false,
      contact : {
        name : '',
        photo : '',
        email : '',
        mobile : '',
        company : '',
        title : '',
        groupId : '',
      },
      errorMessage : null,
      groups : []
    }
  },
  created : async function() {
    try{
      this.loading = true;
      let response = await ContactService.getContact(this.contactId);
      let groupResponse = await ContactService.getAllGroups();
      this.contact = response.data;
      this.groups = groupResponse.data;
      this.loading = false;
    }
    catch (error) {
      this.errorMessage = error;
      this.loading = false;
    }
  },
  methods : {
    updateSubmit : async function () {
      try {
        let response = await ContactService.updateContact(this.contact, this.contactId);
        if (response) {
          return this.$router.push(`/`);
        }
        else {
          return this.$router.push(`/contacts/edit/${this.contactId}`);
        }
      }
      catch (error) {
        console.log(error);
      }
    }
  }
}
</script>

<style scoped>

</style>