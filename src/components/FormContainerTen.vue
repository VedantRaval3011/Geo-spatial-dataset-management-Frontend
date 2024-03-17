<template>
  <div class="form-container-Ten">
    <div class="white-container">
      <div class="heading"><h3>Abstract describing the data</h3></div>
      <div class="dia">
        <label for="dia">Data identification abstract</label>
        <div class="dia-input">
          <input
            type="dia"
            id="dia"
            v-model="dia"
            @input="ValidateDia"
          />
          <i
            v-if="CorrectDia && dia"
            class="fa-solid fa-circle-check"
            id="tick"
          ></i>
          <i
            v-else-if="!CorrectDia && dia"
            class="fa-solid fa-circle-xmark"
            id="cross"
          ></i>
        </div>
      </div>
    </div>
    <div class="bottom-layer">
      <div class="steps">
        <span id="current-step">10</span> of <span id="total-steps">12</span>
      </div>
      <div class="move-icons">
        <i class="fa-solid fa-circle-chevron-left" @click="handleLeftClick"></i>
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
    const dia = ref("");
    const CorrectDia = ref(false);

    const ValidateDia = () => {
      CorrectDia.value = dia.value.length > 1;
    };

    const handleRightClick = () => {
     
        const data = {
        dia: dia.value,
        CorrectDia: CorrectDia.value,
      };

      emit("update-data", data);
        emit("validate-and-proceed-form-ten");
      
    };

    const handleLeftClick = () =>{
      emit("MoveBackToNine");
    }

    return {
      dia,
      v$,
      handleRightClick,
      ValidateDia,
      CorrectDia,
      handleLeftClick
    };
  },
};
</script>
<style scoped>
body {
  padding: 0;
  margin: 0;
}

.form-container-eight {
  position: relative;
  left: 60px;
}

.dia-input {
  position: relative;
}

#tick {
  color: green;
  position: absolute;
  top: 12px;
  right: 20px;
}

#cross {
  color: crimson;
  position: absolute;
  top: 12px;
  right: 20px;
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

.dia {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.heading {
  position: relative;
  right: 85px;
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
  width: 400px;
  height: 41px;
  font-style: italic;
  box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.2);
  text-indent: 22px;
  font-weight: 300;
  box-sizing: border-box;
  margin-left: 4px;
  padding-right: 45px;
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