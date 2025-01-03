<script setup>
useHead({
  title: "SMK Negeri 4 Tasikmalaya",
  meta: [
    {
      name: "description",
      content: "Halaman Beranda",
    },
  ],
});

const supabase = useSupabaseClient();

const berita = ref([]);

const targetNumbers = ref({
  siswa: 1500,
  guru: 82,
  rombel: 45,
  tenagaAdministrasi: 10,
});

const animatedNumbers = ref({
  siswa: 0,
  guru: 0,
  rombel: 0,
  tenagaAdministrasi: 0,
});

const animateNumber = (start, end, key, duration = 2000) => {
  const startTime = performance.now();

  const update = (currentTime) => {
    const elapsedTime = currentTime - startTime;
    const progress = Math.min(elapsedTime / duration, 1); // Pastikan progress tidak lebih dari 1
    animatedNumbers.value[key] = Math.floor(start + (end - start) * progress);

    if (progress < 1) {
      requestAnimationFrame(update);
    }
  };

  requestAnimationFrame(update);
};

const getData = async () => {
  const { data, error } = await supabase
    .from("berita")
    .select(`*, url`)
    .order("id", { ascending: true });

  if (data) berita.value = data;
};

onMounted(() => {
  getData();
  Object.keys(targetNumbers.value).forEach((key) => {
    animateNumber(0, targetNumbers.value[key], key, 2000); // Animasi tiap angka
  });
});
</script>

<template>

  <div class="container-fuild">

    <!--Background Video-->
    <section id="bg">
      <div class="carousel-inner">
        <div class="carousel-item active custom-bg position-relative">
          <video autoplay muted loop class="video-bg position-absolute">
            <source src="assets/video/backgroundvideo.mp4" type="video/mp4" />
            Your browser does not support the video tag.
          </video>
          <div class="overlay position-relative d-flex">
            <div>
              <h5 class="custom-text text-center">
                "Terwujudnya Lulusan yang Cerdas, Aktif, Kompetitif, Adaptif dan
                Produktif Berlandaskan Iman dan Taqwa"
              </h5>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!--Sambutan Kepala Sekolah-->
    <section id="sambutan" class="text-white pt-3 pb-3" style="background-color: #00467d !important">
      <div class="container">
        <h3 class="text-center fw-bold">Sambutan Kepala Sekolah</h3>
        <div class="row">
          <div class="col-lg-4 ">
            <div class="kepsek">
              <img src="/assets/img/kepsek.png" class="img-fluid" alt="kepsek">
            </div>
            <h5 class="pt-3 text-center pe-4">KURNIAWAN S.Pd M.Pd</h5>
          </div>
          <div class="col-lg-8 align-self-center">
            <div class="">
              <h6>Assalamu'alaikum Warahmatullahi Wabarakatuh</h6>
              <p class="lh-base">
                Selamat datang di SMK Negeri 4 TASIKMALAYA. Segala puji dan
                syukur kita panjatkan kehadirat Allah SWT, semoga kita semua ada
                dalam lindungan-Nya. Dan atas perkenan-Nya pula kami dapat
                menghadirkan website SMK Negeri 4 TASIKMALAYA ini. Kami berharap
                dengan adanya website di SMK Negeri 4 TASIKMALAYA ini para
                pengunjung dapat mengenal lebih jauh tentang sekolah kami
                sehingga dapat mempererat tali silaturahmi antara sekolah dengan
                masyarakat demi kemajuan kita bersama. Tiada gading yang tak
                retak, website kami ini masih dalam proses pengembangan, masih
                banyak kekurangan yang harus kami perbaiki. Kritik dan sarannya
                yang membangun sangat kami harapkan untuk pengembangan ke depan.
                Akhirnya, saya mengucapkan terimakasih yang sebesar-besarnya
                kepada semua pihak yang tidak dapat disebutkan satu segala
                bantuan dan persatu atas fasilitasnya yang telah diberikan
                semoga semua yang kita lakukan bermanfaat bagi masyarakat.
              </p>
              <h6 class="">Wassalamu'alaikum Warahmatullahi Wabarakatuh</h6>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Berita Section -->
    <section id="berita" class="berita-section">
      <div class="container">
        <h3 class="text-center fw-bold mb-5" style="color: #00467d !important">
          Berita Terkini
        </h3>
        <div class="row">
          <div v-for="(data, i) in berita" :key="i" class="col-lg-3 pt-3">
            <div class="card berita shadow-lg">
              <div class="overflow-hidden">
                <img :src="data.foto" class="card-img-top" alt="..." />
              </div>

              <div class="card-body">
                <h6 class="card-title">{{ data.judul }}</h6>
                <p class="card-text">
                  {{ data.nama }}
                </p>
                <a :href="data.url" class="btn btn-primary" target="_blank" rel="noopener noreferrer">
                  Baca Selengkapnya
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!--Data Statistik-->
    <section id="data" class="text-white stat" style="background-color: #00467d !important">
      <div class="container">
        <h3 class="text-center fw-bold pb-5">Data Statistik</h3>
        <div class="row">
          <div class="col">
            <h5 class="text-center">Jumlah Siswa</h5>
            <h2 class="text-center display-3">
              {{ animatedNumbers.siswa }}
            </h2>
          </div>
          <div class="col">
            <h5 class="text-center">Guru</h5>
            <h2 class="text-center display-3">
              {{ animatedNumbers.guru }}
            </h2>
          </div>
          <div class="col">
            <h5 class="text-center">Rombel</h5>
            <h2 class="text-center display-3">
              {{ animatedNumbers.rombel }}
            </h2>
          </div>
          <div class="col">
            <h5 class="text-center">Tenaga Administrasi</h5>
            <h2 class="text-center display-3">
              {{ animatedNumbers.tenagaAdministrasi }}
            </h2>
          </div>
        </div>
      </div>
    </section>

    <!--Jurusan Section-->
    <section id="berita" class="jurusan-section">
      <h3 class="text-center fw-bold mb-5" style="color: #00467d !important">
        Program Keahlian
      </h3>
      <div class="container">
        <div class="row d-flex justify-content-around">
          <div class="card mb-3" style="max-width: 540px">
            <div class="row g-0">
              <div class="col-md-4">
                <img src="/assets/img/tejekate.png" class="img-fluid rounded-start" alt="..." />
              </div>
              <div class="col-md-8">
                <div class="card-body">
                  <h5 class="card-title">
                    Teknik Jaringan Komputer dan Telekomunikasi (TJKT)
                  </h5>
                  <p class="card-t</div>ext">
                    Jurusan yang mempelajari tentang ilmu komputerisasi yang
                    meliputi jaringan, perakitan dan perbaikan komputer,
                    troubleshooting, serta konfigurasi perangkat jaringan
                    seperti router dan switch.
                  </p>
                </div>
              </div>
            </div>
          </div>
          <div class="card mb-3" style="max-width: 540px">
            <div class="row g-0">
              <div class="col-md-4">
                <img src="/assets/img/pepeelge.png" class="img-fluid rounded-start" alt="..." />
              </div>
              <div class="col-md-8">
                <div class="card-body">
                  <h5 class="card-title">
                    Pengembangan Perangkat Lunak dan Gim (PPLG)
                  </h5>
                  <p class="card-text">
                    Jurusan yang mempelajari tentang perkembangan perangkat
                    lunak meliputi pembuatan, manajemen organisasi pengembangan
                    perangkat lunak, pemeliharaan dan manajemen kualitas.
                  </p>
                </div>
              </div>
            </div>
          </div>
          <div class="card mb-3" style="max-width: 540px">
            <div class="row g-0">
              <div class="col-md-4">
                <img src="/assets/img/tebeesem.png" class="img-fluid rounded-start" alt="..." />
              </div>
              <div class="col-md-8">
                <div class="card-body">
                  <h5 class="card-title">
                    Teknis dan Bisnis Sepeda Motor (TBSM)
                  </h5>
                  <p class="card-text">
                    Jurusan yang mempelajari tentang merancang, mengembangkan
                    sepeda motor, melakukan perawatan dan perbaikan sepeda
                    motor, juga memodifikasi sepeda motor.
                  </p>
                </div>
              </div>
            </div>
          </div>
          <div class="card mb-3" style="max-width: 540px">
            <div class="row g-0">
              <div class="col-md-4">
                <img src="/assets/img/dekaep.png" class="img-fluid rounded-start" alt="..." />
              </div>
              <div class="col-md-8">
                <div class="card-body">
                  <h5 class="card-title">Desain Komunikasi Visual (DKV)</h5>
                  <p class="card-text">
                    Jurusan yang mempelajari konsep komunikasi melalui berbagai
                    media yang dapat berupa gambar, tatanan huruf, video, media
                    interaktif, dan media visual lainnya.
                  </p>
                </div>
              </div>
            </div>
          </div>
          <div class="card mb-3" style="max-width: 540px">
            <div class="row g-0">
              <div class="col-md-4">
                <img src="/assets/img/teoi.png" class="img-fluid rounded-start" alt="..." />
              </div>
              <div class="col-md-8">
                <div class="card-body">
                  <h5 class="card-title">Teknik Otomasi Industri (TOI)</h5>
                  <p class="card-text">
                    Jurusan yang mempelajari penggabungan ilmu mesin mekanik dan
                    elektronika yang dihubungkan dengan sistem kontrol
                    elektronik dan pneumatik.
                  </p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.lh-base {
  text-align: justify;
  font-size: 100%;
}

.card-text,
.card-title {
  text-align: justify;
}

.stat {
  height: 300px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.left {
  border-right: 1px solid;
}

.custom-bg .video-bg {
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: -1;
}

.custom-bg {
  height: 100vh;
}

.overlay {
  width: 100%;
  height: 100%;
  align-items: center;
  justify-content: center;
  background: rgba(0, 0, 0, 0.5);
}

.custom-text {
  color: white;
  font-size: 1.5rem;
  text-align: center;
  font-weight: bold;
  padding: 20px;
}

.berita {
  transition: transform 0.3s ease, filter 0.3s ease;
}

.berita:hover {
  transform: scale(1);
  filter: brightness(0.9);
}

* {
  text-decoration: none;
}

.berita-section,
.jurusan-section,
.contact-section {
  padding: 40px 20px;
}
</style>
