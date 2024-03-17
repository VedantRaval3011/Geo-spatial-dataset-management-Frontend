<template>
  <div class="ridam-container">
    <div class="top-container">
      <div class="logo">
        <img src="../assets/vedas.png" alt="vedas logo" />
      </div>
      <div class="user">
        <img class="user-button" src="../assets/userbg.png" alt="user-image" />
      </div>
    </div>
    <div class="mid-container">
      <div class="heading"><h1>RIDaM</h1></div>
      <div class="pill-container">
        <div class="pill">
          <p>Raster Analytics System for Interactive Data Modeling</p>
        </div>
      </div>
      <div class="sub-text"><h2>Select the management module</h2></div>
      <ScrollableModule scrollDistance="3000" />
    </div>
    <div class="footer">
      <p class="About-Ridam">About RIDaM</p>
    </div>
  </div>
</template>

<script>
import ScrollableModule from "../components/ScrollableModule.vue";
export default {
  name: "Ridam",
  components: {
    ScrollableModule,
  },
  computed: {
    gradientBackground() {
      return "linear-gradient(to right top, #c3e5f9, #aadffb, #8ed9fc, #6bd4fd, #35cefd)";
    },
  },
};
</script>

<style scoped>
body,
html {
  margin: 0;
  padding: 0;
  height: 100%;
}

.top-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;

  padding: 0;
  background: inherit;
  display: flex;
  justify-content: space-between;
}

.logo {
  margin-right: 20px; /* Add some spacing between the logo and other content */
}

.logo img {
  margin-left: 20px;
}

.user-button {
  width: 80px;
  margin: 33px;
  border-radius: 50%; /* Add rounded corners */
  box-shadow: 0px 1px 5px rgb(94, 77, 77);
}

.user-button:hover {
  box-shadow: 0px 0px 0px rgb(94, 77, 77);
  cursor: pointer;
  z-index: 20;
}

.ridam-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: linear-gradient(
    to right,
    #c3e5f9,
    #bae1f6,
    #b0dcf3,
    #a6d8f0,
    #9cd4ed,
    #93d1eb,
    #89cde8,
    #7fcae6,
    #73c6e4,
    #67c2e3,
    #59bee1,
    #49bae0
  ); /* Gradient background */
}

.mid-container {
  display: flex;
  flex-direction: column;
  z-index: 999;
  text-shadow: 0px 1px 1px #344747;
}

h1 {
  font-size: 41px;
  padding: 0;
  margin: 0;
  margin-bottom: 5px;
}
.pill-container {
  display: flex;
  justify-content: center; /* Align items horizontally to the center */
}

.pill {
  width: 600px; /* Adjust as needed */
  height: 50px; /* Adjust as needed */
  border: none;
  border-radius: 50px; /* Half of the height */
  background: linear-gradient(
    to bottom,
    #b2e2f1,
    #b2e2f1,
    #b2e2f1,
    #b2e2f1,
    #b2e2f1
  ); /* Gradient fill */
  color: #344747;
  font-size: 23px; /* Adjust as needed */
  margin-right: 40px; /* Add gap between buttons */
  font-style: italic;
  box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.2);
  padding: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.pill p {
  margin: 14px;
  font-weight: 600;
  font-size: 20px;
}

.footer {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  position: fixed;
  bottom: 0;
  height: 50px;
  width: 100%;
  background-color: #e7f1f2; /* color */
  z-index: 2;
  box-shadow: 0px 0px 2px rgba(0, 0, 0, 0.5); /* main drop shadow */
}

.About-Ridam {
  margin: 0;
  margin-right: 15px;
  font-weight: 450;
  color: #344747;
}
</style>
