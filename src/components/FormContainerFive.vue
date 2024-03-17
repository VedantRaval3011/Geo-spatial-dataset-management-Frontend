<template>
  <div class="form-container-5">
    <div class="white-container">
        <div class="heading"><h3>Coverage</h3></div>
        <div class="row-1">
            <div class="sub-heading-1"><p>Upper Left</p></div>
            <div class="content-upper-left">
                <div class="x-1">
                    <label for="x-ul">X</label>
                    <input type="text" id="x-ul" v-model="xUl" @input="validateNumberInput(xUl)">
                    <i
                    class="fa-solid fa-circle-check"
                    id="tick-left"
                    v-if="CorrectXUl && xUl"
                    ></i>
                    <i
                    id="cross-left"
                    class="fa-solid fa-circle-xmark"
                    v-if="!CorrectXUl && xUl"
                    ></i>
                </div>
                <div class="y-1">
                    <label for="y-ul">Y</label>
                    <input type="text" id="y-ul" v-model="yUl" @input="validateNumberInput(yUl)">
                    <i
                    class="fa-solid fa-circle-check"
                    id="tick-left"
                    v-if="CorrectYUl && yUl"
                    ></i>
                    <i
                    id="cross-left"
                    class="fa-solid fa-circle-xmark"
                    v-if="!CorrectYUl && yUl"
                    ></i>
                </div>
            </div>
        </div>
        <div class="row-2">
            <div class="sub-heading-2"><p>Upper Right</p></div>
            <div class="content-upper-right">
                <div class="x-2">
                    <label for="x-ur">X</label>
                    <input type="text" id="x-ur" v-model="xUr" @input="validateNumberInput(xUr)">
                    <i
                    class="fa-solid fa-circle-check"
                    id="tick-left"
                    v-if="CorrectXUr && xUr"
                    ></i>
                    <i
                    id="cross-left"
                    class="fa-solid fa-circle-xmark"
                    v-if="!CorrectXUr && xUr"
                    ></i>
                </div>
                <div class="y-2">
                    <label for="y-ur">Y</label> 
                    <input type="text" id="y-ur" v-model="yUr" @input="validateNumberInput(yUr)">
                    <i
                    class="fa-solid fa-circle-check"
                    id="tick-left"
                    v-if="CorrectYUr && yUr"
                    ></i>
                    <i
                    id="cross-left"
                    class="fa-solid fa-circle-xmark"
                    v-if="!CorrectYUr && yUr"
                    ></i>
                </div>
            </div>
        </div>
        <div class="row-3">
            <div class="sub-heading-3"><p>Lower Right</p></div>
            <div class="content-lower-right">
                <div class="x-3">
                    <label for="x-lr">X</label>
                    <input type="text" id="x-lr" v-model="xLr" @input="validateNumberInput(xLr)">
                    <i
                    class="fa-solid fa-circle-check"
                    id="tick-left"
                    v-if="CorrectXlr && xLr"
                    ></i>
                    <i
                    id="cross-left"
                    class="fa-solid fa-circle-xmark"
                    v-if="!CorrectXlr && xLr"
                    ></i>
                </div>
                <div class="y-3">
                    <label for="y-lr">Y</label>
                    <input type="text" id="y-lr" v-model="yLr" @input="validateNumberInput(yLr)">
                    <i
                    class="fa-solid fa-circle-check"
                    id="tick-left"
                    v-if="CorrectYlr && yLr"
                    ></i>
                    <i
                    id="cross-left"
                    class="fa-solid fa-circle-xmark"
                    v-if="!CorrectYlr && yLr"
                    ></i>
                </div>
            </div>
        </div>
        <div class="row-4">
            <div class="sub-heading-4"><p>Lower Left</p></div>
            <div class="content-lower-left">
                <div class="x-4">
                    <label for="x-ll">X</label>
                    <input type="text" id="x-ll" v-model="xLl" @input="validateNumberInput(xLl)">
                    <i
                    class="fa-solid fa-circle-check"
                    id="tick-left"
                    v-if="CorrectXLl && xLl"
                    ></i>
                    <i
                    id="cross-left"
                    class="fa-solid fa-circle-xmark"
                    v-if="!CorrectXLl && xLl"
                    ></i>
                </div>
                <div class="y-4">
                    <label for="y-l">Y</label>
                    <input type="text" id="y-ul" v-model="yLl" @input="validateNumberInput(yUl)">
                    <i
                    class="fa-solid fa-circle-check"
                    id="tick-left"
                    v-if="CorrectYLl && yLl"
                    ></i>
                    <i
                    id="cross-left"
                    class="fa-solid fa-circle-xmark"
                    v-if="!CorrectYLl && yLl"
                    ></i>
                </div>
            </div>
        </div>
    </div>
    <div class="bottom-layer">
      <div class="steps">
        <span id="current-step">5</span> of <span id="total-steps">12</span>
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
import { ref,watch } from "vue";
import useValidate from "@vuelidate/core";
export default {
  setup(prop, { emit }) {
    const yLl = ref("");
    const CorrectYLl = ref(false);
    const xLl = ref("");
    const CorrectXLl = ref(false);
    const yLr = ref("");
    const CorrectYlr = ref(false);
    const xLr = ref("");
    const CorrectXlr = ref(false);
    const xUl = ref("");
    const CorrectXUl = ref(false);
    const yUl = ref("");
    const CorrectYUl = ref(false);
    const xUr = ref("");
    const CorrectXUr = ref(false);
    const yUr = ref("");
    const CorrectYUr = ref(false);
    const v$ = useValidate();

    const validateNumberInput = (input) => {
      return /^-?\d*\.?\d*$/.test(input);
    };
    
    // Watcher for xUl
    watch(xUl, (newValue, oldValue) => {
      if (validateNumberInput(newValue)) {
        CorrectXUl.value = true;
      } else {
        CorrectXUl.value = false;
      }
    });

    // Watcher for yUl
    watch(yUl, (newValue, oldValue) => {
      if (validateNumberInput(newValue)) {
        CorrectYUl.value = true;
      } else {
        CorrectYUl.value = false;
      }
    });

    // Watcher for xUr
    watch(xUr, (newValue, oldValue) => {
      if (validateNumberInput(newValue)) {
        CorrectXUr.value = true;
      } else {
        CorrectXUr.value = false;
      }
    });

    // Watcher for yUr
    watch(yUr, (newValue, oldValue) => {
      if (validateNumberInput(newValue)) {
        CorrectYUr.value = true;
      } else {
        CorrectYUr.value = false;
      }
    });

    // Watcher for xLr
    watch(xLr, (newValue, oldValue) => {
      if (validateNumberInput(newValue)) {
        CorrectXlr.value = true;
      } else {
        CorrectXlr.value = false;
      }
    });

    // Watcher for yLr
    watch(yLr, (newValue, oldValue) => {
      if (validateNumberInput(newValue)) {
        CorrectYlr.value = true;
      } else {
        CorrectYlr.value = false;
      }
    });

    // Watcher for xLl
    watch(xLl, (newValue, oldValue) => {
      if (validateNumberInput(newValue)) {
        CorrectXLl.value = true;
      } else {
        CorrectXLl.value = false;
      }
    });

    // Watcher for yLl
    watch(yLl, (newValue, oldValue) => {
      if (validateNumberInput(newValue)) {
        CorrectYLl.value = true;
      } else {
        CorrectYLl.value = false;
      }
    });

    const handleRightClick = () => {
      // const { emit } = getCurrentInstance(); // Access emit function using getCurrentInstance
      // Emit an event to the parent component to validate and proceed
      // Ensure that the necessary data is filled
      
        // Emit an event to the parent component
        // This event is caught in the parent component to proceed to the next step
        const data = {
        yLl: yLl.value,
        CorrectYLl: CorrectYLl.value,
        xLl: xLl.value,
        CorrectXLl: CorrectXLl.value,
        yLr: yLr.value,
        CorrectYlr: CorrectYlr.value,
        xLr: xLr.value,
        CorrectXlr: CorrectXlr.value,
        xUl: xUl.value,
        CorrectXUl: CorrectXUl.value,
        yUl: yUl.value,
        CorrectYUl: CorrectYUl.value,
        xUr: xUr.value,
        CorrectXUr: CorrectXUr.value,
        yUr: yUr.value,
        CorrectYUr: CorrectYUr.value
      };

       emit("update-data", data);

        console.log("emiting");
        emit("validate-and-proceed-form-five");
        
    };

    const handleLeftClick = () =>{
      emit("MoveBackToFour");
    }

    return {
      v$,
      yLl,
      CorrectYLl,
      xLl,
      CorrectXLl,
      yLr,
      CorrectYlr,
      xLr,
      CorrectXlr,
      xUl,
      CorrectXUl,
      yUl,
      CorrectYUl,
      xUr,
      CorrectXUr,
      yUr,
      CorrectYUr,
      handleRightClick,
      validateNumberInput,
      handleLeftClick,
    };
  },
};
</script>


<style scoped>
    body{
        padding: 0;
        margin: 0;
    }
    .form-container-5{
        display: flex;
        flex-direction: column;
       
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
    width: 458px;
    height: 450px;
    max-width: 100%;
    padding-bottom: 50px;
    margin-left: 78px;

    }

    .heading{
        position: relative;
        right: 130px
    }

    .content-upper-left, .content-lower-left ,.content-lower-right, .content-upper-right{
        display: flex;
        justify-content: space-between;
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
    width: 154px;
    height: 41px;
    font-style: italic;
    box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.2);
    text-indent: 22px;
    font-weight: 300;
    box-sizing: border-box;
    margin-left: 4px;
    }

    .sub-heading-1, .sub-heading-2,.sub-heading-3,.sub-heading-4{
        position: relative;
        right: 120px;
        padding: 0;
        margin: 0;
        top:10px;
    }
    .x-4,.y-4,.x-3,.y-3, .x-2,.y-2, .x-1, .y-1{
        position: relative;
    }

    #tick-left{
        color: green;
        position: absolute;
        right: 10px;
        top: 12px;
    }

    #cross-left{
         color: red;
        position: absolute;
        right: 10px;
        top: 12px;
    }
    
</style>