<template>
  <div class="form-container-four">
    <div class="white-container">
      <div class="heading">
        <h3>Geographic Location</h3>
      </div>
      <div class="row">
        <div class="left">
          <label for="Spheroid">Spheroid</label>
          <div class="input-left">
            <input type="text" v-model="spheroid" />
            <i
              class="fa-solid fa-circle-check"
              id="tick-left"
              v-if="CorrectSpheroid && spheroid"
            ></i>
            <i
              id="cross-left"
              class="fa-solid fa-circle-xmark"
              v-if="!CorrectSpheroid && spheroid"
            ></i>
          </div>
        </div>
        <div class="right">
          <label for="datum">Datum</label>
          <div class="input-right">
            <input type="text" v-model="datum" />
            <i
              class="fa-solid fa-circle-check"
              id="tick-left"
              v-if="CorrectDatum && datum"
            ></i>
            <i
              id="cross-left"
              class="fa-solid fa-circle-xmark"
              v-if="!CorrectDatum && datum"
            ></i>
          </div>
        </div>
      </div>
    </div>
    <div class="bottom-layer">
      <div class="steps">
        <span id="current-step">4</span> of <span id="total-steps">12</span>
      </div>
      <div class="move-icons">
        <i class="fa-solid fa-circle-chevron-left" id="left" @click="handleLeftClick"></i>
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
  setup(prop, { emit }) {
    const spheroid = ref("");
    const CorrectSpheroid = ref(true);
    const datum = ref("");
    const CorrectDatum = ref(true);

    const v$ = useValidate();

    const handleRightClick = () => {
      // const { emit } = getCurrentInstance(); // Access emit function using getCurrentInstance
      // Emit an event to the parent component to validate and proceed
      // Ensure that the necessary data is filled
     
        // Emit an event to the parent component
        // This event is caught in the parent component to proceed to the next step

        const data = {
        
        spheroid: spheroid.value,
        datum: datum.value,
        CorrectDatum: CorrectDatum.value,
        CorrectSpheroid: CorrectSpheroid.value,
        
        
        
      };
      // Emit the 'update-data' event with the updated data
      emit("update-data", data);

        console.log("emiting");
        emit("validate-and-proceed-form-four");
      
    };
    const handleLeftClick = () => {
      emit("MoveBackToThree");
    }

    return {
      v$,
      spheroid,
      datum,
      CorrectDatum,
      CorrectSpheroid,
      handleRightClick,
      handleLeftClick,
    };
  },
};
</script>

<style scoped>
body {
  padding: 0;
  margin: 0;
}

.bottom-layer {
  width: 100%;
  padding: 20px;
  text-align: center;
  font-size: 25px;
  padding-top: 30px;
  display: flex;
  gap: 15px;
  justify-content: center;
}

#right {
  transform: rotate(180deg);
  position: relative;
  left: 5px;
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
  gap: 18px;
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
  padding: 11px 32px 32px 17px;
  max-width: 100%;
}

.row {
  display: flex;
  gap: 35px;
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
  width: 257px;
  height: 41px;
  font-style: italic;
  box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.2);
  text-indent: 22px;
  font-weight: 300;
  box-sizing: border-box;
  margin-left: 4px;
}

.input-left,
.input-right {
  position: relative;
}
.heading h3 {
  position: relative;
  right: 167px;
}

label {
  position: relative;
  bottom: 3px;
  right: 72px;
}

#tick-left {
  position: absolute;
  bottom: 12px;
  color: green;
  right: 10px;
}
#cross-left {
  position: absolute;
  bottom: 12px;
  color: crimson;
  right: 10px;
}
</style>
