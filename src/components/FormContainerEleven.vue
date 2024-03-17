<template>
  <div class="form-container-eleven">
    <div class="white-container">
      <div class="heading">
        <h3>Data Quality</h3>
      </div>
      <div class="process-desc">
        <label for="pd" class="pd-heading">Process Description </label><br />
        <input type="text" id="pd" v-model="pd" @input="ValidatePd" />
        <i
          class="fa-solid fa-circle-check"
          id="tick"
          v-if="Correctpd && pd"
        ></i>
        <i
          id="cross"
          class="fa-solid fa-circle-xmark"
          v-if="!Correctpd && pd"
        ></i>
      </div>
      <div class="report">
        <label for="accReport" class="accR">Source contribution attribute accuracy report</label> <br />
        <input type="text" id="accReport" v-model="accReport" @input="ValidateAccR" /><i
          class="fa-solid fa-circle-check"
          id="tick"
          v-if="CorrectAccR && accReport"
        ></i>
        <i
          id="tick-1"
          class="fa-solid fa-circle-check"
          v-if="!CorrectAccR && accReport"
        ></i>
      </div>

    

      <div class="horpor">
        <label for="horpor" class="heading-horpor">Horizontal positional report accuracy</label><br />
        <input
          type="text"
          id="horpor-input"
          v-model="horpor"
          @input="ValidateHorpor"
        /><i
          class="fa-solid fa-circle-check"
          id="ticklineage"
          v-if="Correcthorpor && horpor"
        ></i>
        <i
          id="cross"
          class="fa-solid fa-circle-xmark"
          v-if="!Correcthorpor && horpor"
        ></i>
      </div>
    </div>
    <div class="bottom-layer">
      <div class="steps">
        <span id="current-step">11</span> of <span id="total-steps">12</span>
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
     <div class="confirmation-checkbox">
      <input type="checkbox" id="confirmation-checkbox" v-model="confirmation" @change="handleConfirmationChange">
      <label for="confirmation-checkbox">Data you have entered is best of your knowledge</label>
    </div>
    
  </div>
</template>

<script>
import { ref, watch } from "vue";
import useValidate from "@vuelidate/core";

export default {
  setup(props, { emit }) {
  const pd = ref("");
  const Correctpd = ref(false);
   const accReport = ref("");
  const CorrectAccR = ref(true);
    const v$ = useValidate();
  const horpor = ref("");
  const Correcthorpor = ref(false);
   const confirmation = ref(false);
 

  const ValidatePd = () => {
    Correctpd.value =  pd.value.length > 3;
  };

  watch(pd, () => {
    ValidatePd();
  });

   const ValidateAccR = () => {
    CorrectAccR.value = accReport.value.length > 3 ;
    console.log(CorrectAccR.value);
  };

  watch(accReport, () => {
    ValidateAccR();
  });

  


  const ValidateHorpor = () => {
    Correcthorpor.value = horpor.value.length > 3;
  };

  watch(horpor, () => {
    ValidateHorpor();
  });


  const handleConfirmationChange = () => {
      if (confirmation.value) {
         const data = {
            pd: pd.value,
            Correctpd: Correctpd.value,
            accReport: accReport.value,
            CorrectAccR: CorrectAccR.value,
            horpor: horpor.value,
            Correcthorpor: Correcthorpor.value
        }
      emit("update-data", data);
      } else {
        alert("Please confirm that the data you have entered is the best of your knowledge.");
      }
    };

  

  const handleRightClick = () => {

   
    emit('validate-and-proceed-form-eleven');   
  };

  const handleLeftClick = () =>{
    console.log('emittt');
    emit('MoveBackToTen');
  }

  return {
    ValidatePd,
    pd,
    confirmation,
    Correctpd,
    ValidateAccR,
    accReport,
    handleConfirmationChange,
    horpor,
    Correcthorpor,
    handleLeftClick,
    v$,
    handleRightClick,
  };
}


}


  

    

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
  margin-left: 164px;
}

#right {
  transform: rotate(180deg);
  position: relative;
  left: 5px;
}

#tick-1{
  color: green;
  position: relative;
  right: 29px;
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

.row {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 20px;
}

#tick{
  position: absolute;
  top: 107px;
  right: 46px;
  color: green;
}

#ticklineage{
  position: absolute;
  top: 257px;
  right: 46px;
  color: green;
}



#tickcn{
  position: absolute;
  top: 409px;
  right: 46px;
  color: green;
}

#tickad{
  position: absolute;
  top: 483px;
  right: 46px;
  color: green;
}



#cross{
  position: relative;
  right: 25px;
  color: crimson;
}

#tick-row{
  position: relative;
  right: 25px;
  color: green;
}
#cross-row{
  position: relative;
  right: 25px;
  color: crimson;
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
  width: 528px;
  height: 41px;
  font-style: italic;
  box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.2);
  text-indent: 22px;
  font-weight: 300;
  box-sizing: border-box;
  margin-left: 4px;
  position: relative;
}

.white-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  border-radius: 56px;
  gap: 15px;
  background: linear-gradient(
    180deg,
    #b2e2f1,
    rgba(178, 226, 241, 0.5) 99.99%,
    rgba(178, 226, 241, 0)
  );
  box-shadow: 0px 4.4px 4.42px rgba(0, 0, 0, 0.25);
  backdrop-filter: blur(9.18px);
  box-sizing: border-box;
  width: 600px;
  padding-bottom: 25px;
  max-width: 100%;
}

#source-scale,
#source-date {
  width: 250px;
}

label {
  position: relative;
  right: 170px;
  margin-bottom: 15px;
}

.row label {
  right: 50px;
}

.heading {
  position: relative;
  right: 200px;
}

.horpor label {
  right: 210px;
}

.accR{
    position: relative;
    left: -54px;
}

.heading-horpor{
    position: relative;
    left: -89px;
}

#confirmation-checkbox{
  padding: 0;
  margin: 0;
  width: 23px;
  height: 23px;
}

.confirmation-checkbox{
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 179px;
  margin-left: 85px;
}

.confirmation-checkbox label{
  margin-top: 15px;
}

.pd-heading{
    position: relative;
    left: -154px;
}
</style>
