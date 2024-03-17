<template>
  <div class="form-container-six">
    <div class="white-container">
      <div class="heading"><h3>Metadata Stamp</h3></div>
      <div class="date">
        <label for="metadata-stamp-date">Metadata Stamp Date</label>
        <div class="date-input">
          <input type="date" id="metadata-stamp-date" v-model="date" />
        </div>
      </div>
    </div>
    <div class="bottom-layer">
      <div class="steps">
        <span id="current-step">6</span> of <span id="total-steps">12</span>
      </div>
      <div class="move-icons">
        <i
          class="fa-solid fa-circle-chevron-left"
          id="left"
          @click="handleLeftCLick"
        ></i>
        <i
          id="right"
          class="fa-solid fa-circle-chevron-left"
          @click="handleRightClick"
        ></i>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
import useValidate from "@vuelidate/core";
export default {
  setup(props, { emit }) {
    const v$ = useValidate();
    const date = ref("");

    const handleRightClick = () => {
      // const { emit } = getCurrentInstance(); // Access emit function using getCurrentInstance
      // Emit an event to the parent component to validate and proceed
      // Ensure that the necessary data is filled

      // Emit an event to the parent component
      // This event is caught in the parent component to proceed to the next step

      const data = {
        date: date.value,
      };

      emit("update-data", data);

      console.log("emiting");
      emit("validate-and-proceed-form-six");
    };
    const handleLeftCLick = () => {
      emit("MoveBackToFive");
    };
    return {
      date,
      v$,
      handleRightClick,
      handleLeftCLick,
    };
  },
};
</script>

<style scoped>
body {
  padding: 0;
  margin: 0;
}

.form-container-six {
  position: relative;
  right: 70px;
}

.bottom-layer {
  width: 100%;
  padding: 20px;
  text-align: center;
  font-size: 25px;
  padding-top: 30px;
  display: flex;
  gap: 15px;
  margin-left: 164px;
}

#right {
  transform: rotate(180deg);
  position: relative;
  left: 5px;
}

.date {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.heading {
  position: relative;
  right: 129px;
}

input {
  background: linear-gradient(
    to bottom,
    #b2e2f1,
    #b2e2f1,
    #b2e2f1,
    #b2e2f1,
    #b2e2f1
  ); /* Gradient fill */
  color: #344747;
  font-size: 17px;
  border: none;
  border-radius: 50px;
  width: 240px;
  height: 41px;
  font-style: italic;
  box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.2);
  text-indent: 22px;
  font-weight: 300;
  box-sizing: border-box;
  margin-left: 4px;
}

#current-step {
  background: linear-gradient(
    to bottom,
    #b2e2f1,
    #b2e2f1,
    #b2e2f1,
    #b2e2f1,
    #b2e2f1
  ); /* Gradient fill */
  padding: 15px 20px 12px 20px;
  border: none;
  border-radius: 16px;
  box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.2);
}

.white-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  border-radius: 56px;
  background: linear-gradient(
    180deg,
    #b2e2f1,
    rgba(178, 226, 241, 0.5) 99.99%,
    rgba(178, 226, 241, 0)
  );
  box-shadow: 0px 4.4px 4.42px rgba(0, 0, 0, 0.25);
  backdrop-filter: blur(9.18px);
  box-sizing: border-box;
  width: 500px;
  padding-bottom: 25px;
  max-width: 100%;
}
</style>