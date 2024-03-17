<template>
  <div class="form-container-extra">
    <div class="extension">
      <label class="extensionText" for="extension">Extension</label>
      <select name="extension" id="extension" v-model="extension">
        <option value="jp2">.jp2</option>
        <option value="tif">.tif</option>
      </select>
    </div>
    <div class="compression">
      <label for="compression" class="compressionText">Compression</label>
      <select name="compression" id="compression" v-model="Compression">
        <option value="jp2000">jp2000</option>
        <option value="deflate">deflate</option>
      </select>
    </div>
    <div class="sampling">
      <label for="sampling" class="SamplingText">Sampling</label>
      <select name="compression" id="sampling" v-model="Sampling">
        <option value="Nearest">Nearest</option>
        <option value="Mode">Mode</option>
        <option value="average">Average</option>
      </select>
    </div>

    <div class="projection">
      <label for="projection" class="ProjectionText">Projection</label>
      <div class="inputs">
        <div class="first">
          <input
            type="text"
            id="projection"
            class="projectOne"
            v-model="Projection"
          />
          <i
            class="fa-solid fa-circle-check"
            id="tick"
            v-if="CorrectProjectOne && Projection"
          ></i>
          <i
            id="cross"
            class="fa-solid fa-circle-xmark"
            v-if="!CorrectProjectOne && Projection"
          ></i>
        </div>

        <button v-if="!showProjection2" @click="addInput">Add</button>
        <div class="second">
          <input
            type="text"
            id="projection"
            class="projectTwo"
            v-model="Projection2"
            v-if="showProjection2"
          />
          <i
            class="fa-solid fa-circle-check"
            id="tick"
            v-if="CorrectProjectTwo && Projection2"
          ></i>
          <i
            id="cross"
            class="fa-solid fa-circle-xmark"
            v-if="!CorrectProjectTwo && Projection2"
          ></i>
        </div>
        <button v-if="!showProjection3 && showProjection2" @click="addInput2">
          Add
        </button>
        <div class="third">
          <input
            type="text"
            id="projection"
            class="projectThree"
            v-model="Projection3"
            v-if="showProjection3"
          />
          <i
            class="fa-solid fa-circle-check"
            id="tick"
            v-if="CorrectProjectThree && Projection3"
          ></i>
          <i
            id="cross"
            class="fa-solid fa-circle-xmark"
            v-if="!CorrectProjectThree && Projection3"
          ></i>
        </div>
      </div>
    </div>
  </div>
  <div class="bottom-layer">
    <div class="steps">
      <span id="current-step">1</span> of <span id="total-steps">12</span>
    </div>
    <div class="move-icons">
      <i
        class="fa-solid fa-circle-chevron-left"
        id="left"
        @click="handleLeftClick"
      ></i>
      <i
        id="right"
        class="fa-solid fa-circle-chevron-left"
        @click="handleRightClick"
      ></i>
    </div>
  </div>
  <input
    type="hidden"
    :value="subtheme"
    @input="updateSubtheme($event.target.value)"
  />
  <input
    type="hidden"
    :value="theme"
    @input="updateTheme($event.target.value)"
  />
</template>

<script>
import { ref, watch } from "vue";
import useValidate from "@vuelidate/core";

export default {
  /*
  // data() {
  //   return {
  //     v$: useValidate(),
  //     Correctprojections: false,
  //     extension: "",
  //     Compression: "",
  //     projection: "",
  //   };
  // },
  validations() {
    return {
      extension: { required },
      Compression: { required },
      projection: { required },
    };
  },
  methods: {
    validateprojections() {
      this.Correctprojections = this.projection.startsWith("/");
    },
  */
  props: ["subtheme", "theme"],

  setup(props, { emit }) {
    const extension = ref("");
    const Compression = ref("");
    const Projection = ref("");
    const Projection2 = ref("");
    const Projection3 = ref("");
    const showProjection3 = ref(false);
    const showProjection2 = ref(false);
    const Sampling = ref("");
    const Correctprojections = ref(false); // Initial validation
    const CorrectProjectOne = ref(false);
    const CorrectProjectTwo = ref(false);
    const CorrectProjectThree = ref(false);

    const v$ = useValidate();
    function addInputWrapper() {}

    const addInput = () => {
      showProjection2.value = true;
    };
    const addInput2 = () => {
      showProjection3.value = true;
    };

    const updateSubtheme = (value) => {
      this.$emit("update:subtheme", value);
    };
    const updateTheme = (value) => {
      this.$emit("update:theme", value);
    };

    const validateProjection = () => {
      CorrectProjectOne.value =
        Projection.value !== Projection2.value &&
        Projection.value !== Projection3.value;
      CorrectProjectTwo.value =
        Projection2.value !== Projection.value &&
        Projection2.value !== Projection3.value;
      CorrectProjectThree.value =
        Projection3.value !== Projection.value &&
        Projection3.value !== Projection2.value;

      if (
        (!CorrectProjectOne.value ||
          !CorrectProjectTwo.value ||
          !CorrectProjectThree.value) &&
        Projection.value.trim() !== "" &&
        Projection2.value.trim() !== "" &&
        Projection3.value.trim() !== ""
      ) {
        alert(
          "Please ensure that the projections are different from each other."
        );
      }
    };

    watch(Projection, validateProjection);
    watch(Projection2, validateProjection);
    watch(Projection3, validateProjection);

    const handleRightClick = () => {
      
      // Emit an event to the parent component to validate and proceed
      

      // Emit an event to the parent component
      // This event is caught in the parent component to proceed to the next step
      console.log("emiting");
      emit(
        "validate-and-proceed",
        subtheme.value,
        theme.value,
        
      );
      const data = {
        subtheme: props.subtheme,
        theme: props.theme,
        extension: extension.value,
        Compression: Compression.value,
        Projection: Projection.value,
        Projection2: Projection2.value,
        Projection3: Projection3.value,
        CorrectProjectOne: CorrectProjectOne.value,
        CorrectProjectTwo: CorrectProjectTwo.value,
        CorrectProjectThree: CorrectProjectThree.value,
        Sampling: Sampling.value
      };
      // Emit the 'update-data' event with the updated data
      emit("update-data", data);
       
      console.log(theme.value);
    };

    const handleLeftClick = () => {
      emit("MoveBackToOne");
    };

    return {
      extension,
      handleLeftClick,
      updateSubtheme,
      updateTheme,
      CorrectProjectOne,
      CorrectProjectThree,
      CorrectProjectTwo,
      Projection2,
      Projection3,
      addInput2,
      Compression,
      addInput,
      Projection,
      Correctprojections,
      addInputWrapper,
      showProjection2,
      showProjection3,
      validateProjection,
      handleRightClick,
      v$,
      Sampling,
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

.form-container-extra {
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

.first,
.second,
.third {
  position: relative;
}

#tick {
  color: green;
  position: absolute;
  z-index: 999;
  right: 9px;
  top: 12px;
}
#cross {
  color: crimson;
  position: absolute;
  z-index: 999;
  right: 10px;
  top: 12px;
}

button {
  --clr-font-main: hsla(0 0% 20% / 100);
  --btn-bg-1: hsla(194 100% 69% / 1);
  --btn-bg-2: hsla(217 100% 56% / 1);
  --btn-bg-color: hsla(360 100% 100% / 1);
  --radii: 0.5em;
  cursor: pointer;

  min-width: 120px;
  min-height: 44px;
  font-size: var(--size, 1rem);
  font-family: "Segoe UI", system-ui, sans-serif;
  font-weight: 500;
  transition: 0.8s;
  background-size: 280% auto;
  background-image: linear-gradient(
    325deg,
    var(--btn-bg-2) 0%,
    var(--btn-bg-1) 55%,
    var(--btn-bg-2) 90%
  );
  border: none;
  width: 50px;
  border-radius: var(--radii);
  color: var(--btn-bg-color);
  box-shadow: 0px 0px 20px rgba(71, 184, 255, 0.5),
    0px 5px 5px -1px rgba(58, 125, 233, 0.25),
    inset 4px 4px 8px rgba(175, 230, 255, 0.5),
    inset -4px -4px 8px rgba(19, 95, 216, 0.35);
}

button:hover {
  background-position: right top;
}

button:is(:focus, :focus-visible, :active) {
  outline: none;
  box-shadow: 0 0 0 3px var(--btn-bg-color), 0 0 0 6px var(--btn-bg-2);
}

@media (prefers-reduced-motion: reduce) {
  button {
    transition: linear;
  }
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

.extensionText,
.compressionText,
.SamplingText {
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

#extension,
#compression,
#sampling {
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

.projection input {
  width: 139px; /* Adjust as needed */
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
  margin-left: 8px;
}

.inputs {
  display: flex;
  gap: 8px;
  justify-content: space-between;
  position: relative;
  left: 174px;
}

.ProjectionText {
  position: fixed;
  left: 45px;
  margin-top: 5px;
  font-weight: 600;
  font-size: 23px;
}

.compression,
.extension {
  display: flex;
  gap: 10px;
}

.sampling {
  display: flex;
  gap: 50px;
}

.projection {
  display: flex;
  justify-content: space-evenly;
  position: relative;
  right: 96px;
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

.extension {
  gap: 52px;
}

.form-container-extra {
  display: flex;
  flex-direction: column;
}

.projection-wrapper {
  display: flex;
  flex-wrap: wrap;
}

.input-wrapper {
  display: flex;
  align-items: center;
}

.add-button {
  width: 120px; /* Adjust the width as needed */
  margin-top: 10px;
}
</style>
