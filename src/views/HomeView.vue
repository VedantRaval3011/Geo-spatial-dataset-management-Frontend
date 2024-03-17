<template>
  <div class="screen-container">
    <div class="home-container">
      <div class="top-container">
        <div class="logo">
          <img src="../assets/vedas.png" alt="vedas logo" />
        </div>
        <div class="login">
          <button class="login-button"><span>LOGIN</span></button>
        </div>
      </div>
      <div class="center-container">
        <!-- Your main content goes here -->
        <h1 class="textVedas">Vedas Geo-spatial Dataset Management System</h1>
        <div class="buttons-container">
          <button class="ridam">
            <router-link to="/ridam" class="ridamrouter">RIDaM</router-link>
          </button>
          <button class="geo-entity-state-system" disabled>
            Geo-entity Stats System
          </button>
        </div>
      </div>
      <div class="footer">
        <p class="help-manual">Help Manual</p>
      </div>
      <div class="half-oval"></div>
    </div>
  </div>
</template>

<script>
 


export default {
  name: "HomeView",
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
  z-index: 999; /* Ensure it's above other content */
  padding: 0;
  background: inherit;
  display: flex;
  gap: 900px;
}

.logo {
  margin-right: 20px; /* Add some spacing between the logo and other content */
}

.logo img {
  margin-left: 20px;
}

.home-container {
  margin-top: 100px; /* Adjust as needed to create space below the top container */
  width: inherit;
}

.footer {
  display: flex;
  justify-content: flex-end;
  align-items: center;
  position: fixed;
  bottom: 0;
  width: 100%;
  background-color: #e7f1f2; /* color */
  padding: 10px; /* Adjust as needed */
  z-index: 2;
  box-shadow: 0px 0px 2px rgba(0, 0, 0, 0.5); /* main drop shadow */
}

.help-manual {
  margin: 0;
  margin-right: 26px;
  font-weight: 450;
  color: #344747;
}

.home-container {
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

.center-container {
  text-align: center;
  position: absolute;
  top: 285px;
}

.textVedas {
  font-size: 35px; /* Adjust as needed */
  color: #344747;
  text-shadow: 1px 1px 2px #344747;
}

.buttons-container {
  display: flex;
  flex-direction: row; /* Set flex direction to row */
  justify-content: center;
  align-items: center;
  margin-top: 20px; /* Adjust as needed */
}

button {
  width: 300px; /* Adjust as needed */
  height: 61px; /* Adjust as needed */
  border: none;
  border-radius: 50px; /* Half of the height */
  background: linear-gradient(
    to bottom,
    #c3e5f9,
    #c3e5f9,
    #c3e5f9,
    #c3e5f9,
    #c3e5f9
  ); /* Gradient fill */
  color: #344747;
  font-size: 23px; /* Adjust as needed */
  margin-right: 40px; /* Add gap between buttons */
  font-style: italic;
  box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.2);
}

.login-button {
  position: absolute;
  right: 52px;
  top: 57px;
  font-size: 15px;
  width: 80px;
  height: 40px;
}

button:disabled {
  opacity: 0.5; /* Adjust the opacity to your liking */
  cursor: not-allowed; /* Change cursor to indicate it's not clickable */
  /* Add any additional styling you want for disabled buttons */
}

.ridam {
  width: 120px;
}

button:last-child {
  margin-right: 0; /* Remove margin from last button */
}

button:hover {
  /* background: linear-gradient(180deg, #87CEEB, #87CEEB ); Adjust gradient on hover */
  box-shadow: 0px 5px 10px rgba(0, 0, 0, 0);
}

.half-oval {
  position: absolute;
  bottom: -792px; /* Adjust the size of the oval */
  left: 50%;
  transform: translateX(-50%);
  width: 2307px; /* Adjust the width of the oval */
  height: 1000px; /* Adjust the height of the oval */
  border-radius: 50%;
  background-color: #eaeef1;
  filter: blur(202px); /* Apply blur */
  z-index: 1; /* Ensure it's behind other content */
}

.ridamrouter {
  text-decoration: none;
  color: inherit;
}

.logo {
  margin-right: 0; /* Remove margin */
}
</style>
