<script setup>
useHead({
  title: "Galeri",
  meta: [
    {
      name: "description",
      content: "Halaman Galeri",
    },
  ],
});

const supabase = useSupabaseClient();

const galeri = ref([]);

const getData = async () => {
  const { data } = await supabase
    .from("galeri")
    .select(`*`)
    .order("id", { ascending: true });
  if (data) galeri.value = data;
  s;
};

onMounted(() => {
  getData();
});
</script>

<template>
  <div class="container pt-3">
    <div class="row">
      <h4 class="text-center" style="color: #00467d !important">
        Galeri Kegiatan
      </h4>
      <div v-for="(get, i) in galeri" :key="i" class="col-lg-4 pt-3">
        <div class="card shadow-lg">
          <img :src="get.foto" class="card-img d flex" alt="..." />
        </div>
      </div>
    </div>
  </div>
</template>
