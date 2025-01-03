<template>
  <div class="container">
    <div class="row d-flex justify-content-center">
      <h4 class="text-center pt-3" style="color: #00467d !important">
        Ekstrakurikuler
      </h4>
      <div v-for="(get, i) in eskul" :key="i" class="col-lg-4 d-flex justify-content-center pt-3">
        <div class="card" style="width: 18rem;">
          <img :src="get.foto" class="card-img-top" alt="...">
          <div class="card-body">
            <p class="card-text text-center">{{ get.nama }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
useHead({
  title: "Ekstrakurikuler",
  meta: [
    {
      name: "description",
      content: "Halaman Ekstrakurikuler",
    },
  ],
});

const supabase = useSupabaseClient()

const eskul = ref([])

const getEskul = async () => {
  const { data } = await supabase.from("eskul").select(`*, nama`).order("id", { ascending: true })
  if (data) eskul.value = data
}

onMounted(() => {
  getEskul()
})
</script>
