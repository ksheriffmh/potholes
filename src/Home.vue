<template>
  <div>
    <div :class="{ 'd-none': !showSplash }">
      <splash-screen></splash-screen>
    </div>
    <div :class="{ 'd-none': showSplash }">
      <iframe
        src="https://maps.google.com/maps?q=12.9847401,80.2459132&hl=en&z=14&amp;output=embed"
        id="map-frame"
        style="border: 0"
        allowfullscreen="true"
        loading="lazy"
        referrerpolicy="no-referrer-when-downgrade"
      ></iframe>
      <button @click="openOptions" class="btn-primary" id="report-btn">Report a Case</button>
    </div>
    <upload-image></upload-image>
    <location></location>
    <user-details></user-details>
    <description></description>
    
  </div>
</template>

<script>
import UploadImage from "./components/UploadImage.vue";
import Location from "./components/Location.vue";
import Description from "./components/Description.vue";
import UserDetails from "./components/UserDetails.vue";
import SplashScreen from "./components/SplashScreen.vue";

export default {
  name: "App",
  components: {
    UploadImage,
    Location,
    UserDetails,
    Description,
    SplashScreen
  },
  data() {
    return {
      showSplash: true,
    };
  },
  mounted() {
    let map = document.getElementById("map-frame");
    map.style.width = window.innerWidth.toString() + "px";
    map.style.height = "90vh";
    setTimeout(() => {
      this.showSplash = false;
    }, 2000);
  },
  methods: {
    openOptions() {
      document.getElementById("map-frame").style.height = "60vh";
      document.getElementById("pull-up-block").classList.remove("hide");
      document.getElementById("report-btn").classList.add("d-none");
      document.getElementById("pull-up-block").classList.add("show");
    },
  },
};
</script>

<style>
@import url(https://fonts.googleapis.com/css?family=Playfair+Display:700italic|Fauna+One);
body {
  margin: 0;
  position: fixed;
  top: 0;
  bottom: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.btn-primary {
  font-family: "Montesserat", "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell,
    "Open Sans", "Helvetica Neue", sans-serif;
  font-weight: 500;
  font-size: 22px;
  color: #fff;
  background: #73ddc1;
  border: 0;
  box-shadow: 0px 0px 8px rgba(0, 0, 0, 0.2);
  width: 100vw;
  height: 80px;
  padding: 5px;
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
}
.d-none {
  display: none;
}
.d-block {
  display: block;
}
</style>
