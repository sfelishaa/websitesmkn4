<template>
  <nav class="navbar navbar-expand-lg navbar-light shadow sticky-top" style="background-color: #ffffff">
    <div class="container">
      <a class="navbar-brand" href="#">
        <img src="~/assets/img/logo.png" alt="Logo" class="align-text-top ms-3" width="45" />
      </a>
      <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav"
        aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav ms-auto">
          <nuxt-link to="/">
            <li class="nav-item">
              <a class="nav-link active" aria-current="page">Beranda</a>
            </li>
          </nuxt-link>

          <nuxt-link to="/profile">
            <li class="nav-item dropdown">
              <a class="nav-link active dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown"
                aria-expanded="false">
                Profile
              </a>
              <ul class="dropdown-menu shadow-lg">
                <nuxt-link to="/profile/identitas">
                  <li>
                    <a class="dropdown-item" href="">Identitas Sekolah</a>
                  </li>
                </nuxt-link>
                <nuxt-link to="/profile/sejarah">
                  <li>
                    <a class="dropdown-item" href="">Sejarah & Visi Misi</a>
                  </li>
                </nuxt-link>
                <nuxt-link to="/profile/guru">
                  <li><a class="dropdown-item" href="#">Guru & Staf</a></li>
                </nuxt-link>
              </ul>
            </li>
          </nuxt-link>

          <nuxt-link to="/galeri">
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="">Galeri</a>
            </li>
          </nuxt-link>

          <nuxt-link to="/eskul">
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="">Ekstrakurikuler</a>
            </li>
          </nuxt-link>

          <nuxt-link to="/kontak">
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="">Kontak</a>
            </li>
          </nuxt-link>
        </ul>
      </div>
    </div>
  </nav>
</template>

<style scoped>
* {
  text-decoration: none;
}
</style>