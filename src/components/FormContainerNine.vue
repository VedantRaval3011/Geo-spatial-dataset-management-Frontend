<template>
  <div class="form-container-nine">
    <div class="white-container">
      <div class="heading"><h3>Launguage</h3></div>
      <div class="language">
        <label for="bsh">Language ISO 0639-2Bsh</label>
        <div class="language-input">
          <input
            type="language"
            id="bsh"
            v-model="language"
            @input="Validatelanguage"
          />
          <i
            v-if="Correctlanguage && language"
            class="fa-solid fa-circle-check"
            id="tick"
          ></i>
          <i
            v-else-if="!Correctlanguage && language"
            class="fa-solid fa-circle-xmark"
            id="cross"
          ></i>
        </div>
      </div>
    </div>
    <div class="bottom-layer">
      <div class="steps">
        <span id="current-step">9</span> of <span id="total-steps">12</span>
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
    const language = ref("");
    const Correctlanguage = ref(false);

    const Validatelanguage = () => {
      Correctlanguage.value = language.value.length > 1;
    };

    const handleRightClick = () => {

      const data = {
        language: language.value,
        Correctlanguage: Correctlanguage.value,
      };

      emit("update-data", data);
     
        emit("validate-and-proceed-form-nine");

      
    };

    const handleLeftClick = () =>{
      emit("MoveBackToEight");
      console.log("emittiiing");
    }

    return {
      language,
      v$,
      handleRightClick,
      Validatelanguage,
      Correctlanguage,
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

.form-container-eight {
  position: relative;
  left: 60px;
}

.language-input {
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

.language {
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
  width: 400px;
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