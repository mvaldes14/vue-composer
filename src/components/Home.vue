<template>
  <div>
    <NavBar />
    <section>
      <Main />
    </section>
    <Footer />
  </div>
</template>

<script>
import NavBar from "./shared/Navbar";
import Footer from "./shared/Footer";
import Main from "./Main";

export default {
  name: "Home",
  components: {
    NavBar,
    Main,
    Footer,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
