<template>
  <div>
    <div class="container mt-3">
      <div class="row">
        <div class="col">
          <p class="h3 text-success fw-bold">Add Contact</p>
          <p class="fst-itailic">Lorem ipsum dolor sit amet consectetur adipisicing elit. Recusandae molestias aperiam ex ipsum possimus explicabo reiciendis velit debitis laudantium sequi natus sit culpa quas, ducimus perspiciatis architecto, fugiat praesentium deleniti!</p>
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
              <input type="submit" class="btn btn-success" value="Create">
            </div>
          </form>
        </div>
        <div class="col-md-4">
          <img src="https://cdn-icons-png.flaticon.com/512/219/219969.png" alt="" class="contact-img"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AddContact"
}
</script>

<style scoped>

</style>