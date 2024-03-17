<template>
  <div class="scrollbar" :style="{ backgroundColor: backgroundColor }">
    <div class="left-scroll" @click="scrollToLeft">
      <img src="../assets/left-arrow.png" alt="left-arrow" />
    </div>
    <div class="container-1" ref="container">
      <div class="primary-data-management">
        <h3>Primary Data Management</h3>
        <p class="pdm-text">
          Lorem ipsum cing elit, sed eiusmod tem incididunt
        </p>
        <span><button class="get-stared-pdm" @click="$router.push('/primary-data-main-page')">Get Started</button></span>
      </div>
      <div class="Shard-Management">
        <h3>Shard Management</h3>
        <p class="pdm-text">
          Lorem ipsum cing elit, sed eiusmod tem incididunt
        </p>
        <span><button class="get-stared-sm" >Get Started</button></span>
      </div>
      <div class="Pyramind-Mangement">
        <h3>Pyramind Mangement</h3>
        <p class="pdm-text">
          Lorem ipsum cing elit, sed eiusmod tem incididunt
        </p>
        <span><button class="get-stared-pym">Get Started</button></span>
      </div>
      <div class="Pool-Managment">
        <h3>
          Pool <br />
          Managment
        </h3>
        <p class="pdm-text">
          Lorem ipsum cing elit, sed eiusmod tem incididunt
        </p>
        <span><button class="get-stared-pom">Get Started</button></span>
      </div>
      <div class="Registry-Management">
        <h3>Registry Management</h3>
        <p class="pdm-text">
          Lorem ipsum cing elit, sed eiusmod tem incididunt
        </p>
        <span><button class="get-stared-rm">Get Started</button></span>
      </div>
      <div class="any1-Management">
        <h3>
          any1 <br />
          Management
        </h3>
        <p class="pdm-text">
          Lorem ipsum cing elit, sed eiusmod tem incididunt
        </p>
        <span><button class="get-stared-a1m">Get Started</button></span>
      </div>
    </div>

    <!-- <div class="container-2">
                
                <div class="any2-Management">
            <h3>any2 <br> Management</h3>
            <p class="pdm-text">Lorem ipsum cing elit, sed eiusmod tem incididunt</p>
            <span><button class="get-stared">Get Started</button></span>
            </div> -->
    <!-- </div> -->
    <div class="right-scroll" @click="scrollToRight">
      <img src="../assets/left-arrow.png" alt="left-arrow" />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    backgroundColor: {
      type: String,
      default: "transparent", // Set default value if not provided
    },
    scrollDistance: {
      // Optional prop for flexible scroll distance
      type: Number,
      default: 100,
    },
  },

  methods: {
    scrollToLeft() {
      const container = this.$refs.container;
      const distance = container.scrollLeft - this.scrollDistance; // Adjustment
      container.scrollTo({
        left: distance,
        behavior: "smooth",
      });
    },

    scrollToRight() {
      const container = this.$refs.container;
      const distance = container.scrollLeft + this.scrollDistance; // Adjustment
      container.scrollTo({
        left: distance,
        behavior: "smooth",
      });
    },
  },
};
</script>

<style scoped>
.scrollbar {
  display: flex;
  background-color: transparent;
  gap: 20px;
  position: relative;
  padding: 20px;
  height: 400px;
  width: calc(6 * 200px + 5 * 20px);
  justify-content: center;
  text-shadow: none;
}

.primary-data-management,
.Shard-Management,
.Registry-Management,
.Pyramind-Mangement,
.Pool-Managment,
.any2-Management,
.any1-Management {
  display: flex;
  flex-direction: column;
  width: 200px;
  height: 315px;
  /* justify-content: space-around; */
  /* height: 260px; */
  padding: 10px;
  padding-bottom: 0;
  border-radius: 56px;
  background: linear-gradient(
    180deg,
    #f8eef3,
    #5dcdf8 0.01%,
    rgba(223, 239, 246, 0.95) 0.02%,
    rgba(242, 249, 251, 0.38) 99.99%,
    rgba(255, 255, 255, 0)
  );
 
  backdrop-filter: blur(25.09px);
  border: 1px solid var(rgba(242, 159, 255, 0.2));
  box-sizing: border-box;
}

.left-scroll img {
  margin-top: 115px;
  width: 44px;
  height: 50px;
}

.scrollbar span {
  padding: 20px;
}

.scrollbar button {
  height: 52px;
  width: 133px;
  position: relative;
  border-radius: 30px;
  /* background: linear-gradient(180deg, #eff7f6, rgba(239, 247, 246, 0)); */
  border: none;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  font-size: 17px;
  font-style: italic;
}

.pdm-text {
  width: 120px;
  margin-left: 27px;
}

.right-scroll {
  transform: rotate(180deg);
}

.right-scroll img {
  margin-top: 236px;
  width: 44px;
  height: 50px;
}

.left-scroll,
.right-scroll {
  cursor: pointer;
}

.container-1 {
  display: flex;
  flex-direction: row;
  gap: 20px;
  overflow-x: scroll;
  
  padding: 10px;
  width: 1046px;
}

.container-1::-webkit-scrollbar {
  width: 8px;
  height: 8px;
}

button{
  cursor: pointer;
}




</style>
