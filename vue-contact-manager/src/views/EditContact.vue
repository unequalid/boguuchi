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
          <form>
            <div class="mb-2">
              <input type="text" class="form-control" placeholder="Name">
            </div>
            <div class="mb-2">
              <input type="text" class="form-control" placeholder="Photo URL">
            </div>
            <div class="mb-2">
              <input type="text" class="form-control" placeholder="Email">
            </div>
            <div class="mb-2">
              <input type="number" class="form-control" placeholder="Mobile">
            </div>
            <div class="mb-2">
              <input type="text" class="form-control" placeholder="Company">
            </div>
            <div class="mb-2">
              <input type="text" class="form-control" placeholder="Title">
            </div>
            <div class="mb-2">
              <select class="form-control">
                <option value="">Select Group</option>
              </select>
            </div>
            <div class="mb-2">
              <input type="submit" class="btn btn-success" value="Update">
            </div>
          </form>
        </div>
        <div class="col-md-4">
          <img src="https://cdn-icons-png.flaticon.com/512/219/219969.png" alt="" class="contact-img"/>
        </div>
      </div>
    </div>
  <pre>{{contact}}</pre>
  <pre>{{group}}</pre>
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
      contact : {},
      errorMessage : null,
      group : {}
    }
  },
  created : async function() {
    try{
      this.loading = true;
      let response = await ContactService.getContact(this.contactId);
      let groupResponse = await ContactService.getGroup(response.data);
      this.contact = response.data;
      this.group = groupResponse.data;
      this.loading = false;
    }
    catch (error) {
      this.errorMessage = error;
      this.loading = false;
    }
  }
}
</script>

<style scoped>

</style>