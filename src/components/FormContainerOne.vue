<template>
  <div class="form-container-one">
    <div class="theme">
      <label class="themetext" for="theme">Theme</label>
      <select name="theme" id="theme" v-model="theme">
        <option value="Land-Use_Land_Cover(50k)1997-2002">
          Land-Use_Land_Cover(50k)1997-2002
        </option>
        <option value="2">2</option>
        <option value="3">3</option>
        <option value="4">4</option>
        <option value="5">5</option>
        <option value="6">6</option>
        <option value="7">7</option>
        <option value="8">8</option>
        <option value="9">9</option>
        <option value="10">10</option>
        <option value="11">11</option>
        <option value="12">12</option>
        <option value="13">13</option>
        <option value="14">14</option>
        <option value="15">15</option>
        <option value="16">16</option>
        <option value="17">17</option>
        <option value="18">18</option>
        <option value="19">19</option>
      </select>
    </div>
    <div class="subtheme">
      <label for="subtheme" class="subthemetext">subtheme</label>
      <select name="subtheme" id="subtheme" v-model="subtheme">
        <option value="gujarat">Gujarat</option>
        <option value="2">2</option>
        <option value="3">3</option>
        <option value="4">4</option>
        <option value="5">5</option>
        <option value="6">6</option>
        <option value="7">7</option>
        <option value="8">8</option>
        <option value="9">9</option>
        <option value="10">10</option>
        <option value="11">11</option>
        <option value="12">12</option>
        <option value="13">13</option>
        <option value="14">14</option>
        <option value="15">15</option>
        <option value="16">16</option>
        <option value="17">17</option>
        <option value="18">18</option>
        <option value="19">19</option>
      </select>
    </div>
    <div class="basepath">
      <label for="basepath" class="base-path-text">Base Path</label>
      <div class="input-wrapper">
        <input type="text" v-model="BasePath" @input="validateBasePath" /><i
          id="correct"
          class="fa-solid fa-check"
          v-if="CorrectBasePath && BasePath"
        ></i>
        <i
          id="cross"
          class="fa-solid fa-circle-xmark"
          v-if="!CorrectBasePath && BasePath"
        ></i>
      </div>
    </div>
  </div>
  <div class="bottom-layer">
    <div class="steps">
      <span id="current-step">1</span> of <span id="total-steps">12</span>
    </div>
    <div class="move-icons">
      <i class="fa-solid fa-circle-chevron-left" id="left"></i>
      <i
        id="right"
        class="fa-solid fa-circle-chevron-left"
        @click="handleRightClick"
      ></i>
    </div>
  </div>
</template>

<script>
import { ref, getCurrentInstance } from "vue";
import useValidate from "@vuelidate/core";
import { required } from "@vuelidate/validators";
export default {
  /*
  // data() {
  //   return {
  //     v$: useValidate(),
  //     CorrectBasePath: false,
  //     theme: "",
  //     subtheme: "",
  //     BasePath: "",
  //   };
  // },
  validations() {
    return {
      theme: { required },
      subtheme: { required },
      BasePath: { required },
    };
  },
  methods: {
    validateBasePath() {
      this.CorrectBasePath = this.BasePath.startsWith("/");
    },
  */

  setup(props, { emit }) {
    const theme = ref("");
    const subtheme = ref("");
    const BasePath = ref("");
    const CorrectBasePath = ref(false);
    const v$ = useValidate();

    function validateBasePath() {
      CorrectBasePath.value = BasePath.value.startsWith("/");
    }

    const handleRightClick = () => {
      // const { emit } = getCurrentInstance(); // Access emit function using getCurrentInstance
      // Emit an event to the parent component to validate and proceed
      // Ensure that the necessary data is filled

      // Emit an event to the parent component
      // This event is caught in the parent component to proceed to the next step
      console.log("emiting");

      const data = {
        subtheme: subtheme.value,
        theme: theme.value,
        BasePath: BasePath.value,
        
      };
      // Emit the 'update-data' event with the updated data
      emit("update-data", data);
      
      emit("validate-and-proceed", subtheme.value, theme.value, BasePath.value);

      console.log(theme.value);
    };

    return {
      theme,
      subtheme,
      BasePath,
      CorrectBasePath,
      validateBasePath,
      handleRightClick,
      v$,
    };
  },
};
</script>

<style scoped>
body {
  margin: 0;
  padding: 0;
  height: 100%;
}

.form-container-one {
  display: flex;
  flex-direction: column;
  gap: 20px;
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
  padding: 35px 27px 37px 44px;
  max-width: 100%;
}

#correct {
  color: green;
  position: relative;
  z-index: 999;
  font-size: 25px;
  right: 42px;
  top: 7.5px;
}
#cross {
  color: crimson;
  position: relative;
  z-index: 999;
  font-size: 25px;
  right: 42px;
  top: 3.5px;
}

#left {
  opacity: 0.8;
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

.themetext,
.subthemetext {
  margin-top: 5px;
  font-weight: 600;
  font-size: 23px;
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

#theme,
#subtheme {
  width: 439px; /* Adjust as needed */
  height: 41px; /* Adjust as needed */
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
  font-size: 17px;
  text-indent: 10px;
  font-style: italic;
  box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.2);
  padding: 5px;
  font-weight: 300;
}

.basepath input {
  width: 439px; /* Adjust as needed */
  height: 41px; /* Adjust as needed */
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
  font-size: 17px;
  padding: 0;
  font-style: italic;
  box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.2);
  text-indent: 22px;
  font-weight: 300;
  box-sizing: border-box;
  margin-left: 4px;
}

.base-path-text {
  margin-top: 5px;
  font-weight: 600;
  font-size: 23px;
}

.subtheme,
.basepath,
.theme {
  display: flex;
  gap: 10px;
}

.basepath {
  box-sizing: border-box;
}

select {
  padding-right: 25px;
  box-sizing: border-box;
}

#right {
  transform: rotate(180deg);
  position: relative;
  left: 5px;
}

.theme {
  gap: 52px;
}
</style>
