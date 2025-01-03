<script setup>
useHead({
  title: "Kontak",
  meta: [
    {
      name: "description",
      content: "Halaman Kontak",
    },
  ],
});

</script>


<template>
  <div class="container pt-3">
    <h4 class="text-center" style="color: #00467d !important">
      Hubungi Kami
    </h4>
    <div class="row">
      <form>
        <div class="mb-3">
          <label for="exampleInputEmail1" class="form-label">Nama</label>
          <input type="text" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
        </div>
        <div class="mb-3">
          <label for="exampleInputEmail1" class="form-label">Email</label>
          <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp">
        </div>
        <div class="mb-3">
          <label for="floatingTextarea2">Pesan</label>
          <textarea class="form-control" id="floatingTextarea2" style="height: 100px"></textarea>
        </div>
        <button type="submit" class="btn btn-primary">Kirim</button>
      </form>
    </div>
  </div>
</template>