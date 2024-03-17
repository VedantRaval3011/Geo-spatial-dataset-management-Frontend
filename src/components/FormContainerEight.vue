<template>
  <div class="form-container-eight">
    <div class="white-container">
      <div class="heading"><h3>Data Topic Category</h3></div>
      <div class="DITC">
        <label for="topic-category">Data identification topic category</label>
        <div class="DITC-input">
          <input
            type="DITC"
            id="topic-category"
            v-model="DITC"
            @input="ValidateDitc"
          />
          <i
            v-if="CorrectDitc && DITC"
            class="fa-solid fa-circle-check"
            id="tick"
          ></i>
          <i
            v-else-if="!CorrectDitc && DITC"
            class="fa-solid fa-circle-xmark"
            id="cross"
          ></i>
        </div>
      </div>
    </div>
    <div class="bottom-layer">
      <div class="steps">
        <span id="current-step">8</span> of <span id="total-steps">12</span>
      </div>
      <div class="move-icons">
        <i class="fa-solid fa-circle-chevron-left" id="left" @click="handleLeftCLick"></i>
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
    const DITC = ref("");
    const CorrectDitc = ref(false);

    const ValidateDitc = () => {
      CorrectDitc.value = DITC.value.length > 1;
    };

    const handleRightClick = () => {

      const data = {
        DITC: dpb.value,
        
      };

      emit("update-data", data);
      
        emit("validate-and-proceed-form-eight");
      
    };
    const handleLeftCLick= () =>{
      emit("MoveBackToSeven");
    }

    return {
      DITC,
      v$,
      handleRightClick,
      ValidateDitc,
      CorrectDitc,
      handleLeftCLick
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

.DITC-input {
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

.DITC {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.heading {
  position: relative;
  right: 120px;
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