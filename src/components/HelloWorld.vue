<template>
  <div>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">Navbar</a>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav me-auto mb-2 mb-lg-0">
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="#">Offers</a>
            </li>

            <li class="nav-item"></li>
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="#">Manage</a>
            </li>

            <li class="nav-item"></li>
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="#"
                >Experience</a
              >
            </li>

            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="#"
                >Marco Polo club</a
              >
            </li>

            <li class="nav-item"></li>
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="#"
                >Business</a
              >
            </li>

            <li class="nav-item"></li>

            <li class="nav-item">
              <a class="nav-link" href="#">Link</a>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </div>
</template>



<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      msg: "Sonom Rubayat",
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
