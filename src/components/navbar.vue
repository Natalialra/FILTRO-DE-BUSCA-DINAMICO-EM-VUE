<template>
  <nav class="navbar navbar-expand-lg fixed-top navbar-light" id="navi">
    <div class="container-fluid">
      <a class="navbar-brand" href="#" id="nav-menu">Logo</a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNavAltMarkup"
        aria-controls="navbarNavAltMarkup"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div
        class="collapse navbar-collapse justify-content-end"
        id="navbarNavAltMarkup"
      >
        <div class="navbar-nav">
          <a
            class="nav-link active mx-3"
            id="nav-menu"
            aria-current="page"
            href="#"
            >Sobre</a
          >
          <a class="nav-link mx-3" id="nav-menu" href="#">Imoveis</a>
          <a class="nav-link mx-3" id="nav-menu" href="#">Contato</a>
        </div>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Navbar",
};
</script>

<style scoped>
#navi {
  background-color: rgb(52, 175, 247);
  border-bottom-left-radius: 10px;
  border-bottom-right-radius: 10px;
  font-family: "Anek Kannada", sans-serif;
  font-size: 1.3rem;
}

#nav-menu {
  color: White;
}

#nav-menu:hover {
  color: black;
  border-bottom: 2px solid black;
}
</style>