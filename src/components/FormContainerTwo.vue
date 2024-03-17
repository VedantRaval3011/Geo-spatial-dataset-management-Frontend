<template>
  <div class="form-container-two">
    <h1>Meta Data of the state: {{ subtheme }}</h1>
    
    <div class="white-container">
      <div class="heading">Data Identification Information</div>
      <div class="name-of-dataset">
        <label for="nom" class="nom">Name of Dataset</label><br />
        <div class="nom-input">
          <input type="text" id="nom" :value="subtheme" readonly /><i
            class="fa-solid fa-circle-check"
            id="tick-nom"
          ></i>
        </div>
      </div>
      <div class="theme">
        <label for="theme" class="themelabel">Theme</label><br />
        <input type="text" id="theme" :value="theme" readonly /><i
          class="fa-solid fa-circle-check"
          id="tick-theme"
        ></i>
      </div>
      <div class="keywords">
        <label class="keyword-heading">Keywords</label> <br />
        <div class="boxes">
          <!-- <div class="row-one">
          <input type="text" class="keyword-box" id="firstbox" v-model="KeywordOne"> <i class="fa-solid fa-circle-check" id="tick-box-1" v-if="CorrectKeywordOne && KeywordOne"  ></i>
          <i
          id="cross-1"
          class="fa-solid fa-circle-xmark"
          v-if="!CorrectKeywordOne && KeywordOne"
        ></i>
          <input type="text" class="keyword-box" id="secondbox" v-model="KeywordTwo"><i class="fa-solid fa-circle-check" id="tick-box-2" v-if="CorrectKeywordTwo && KeywordTwo"></i>
          <i
          id="cross-2"
          class="fa-solid fa-circle-xmark"
          v-if="!CorrectKeywordTwo && KeywordTwo"
        ></i>
          <input type="text" class="keyword-box" id="thirdbox" v-model="KeywordThree"><i class="fa-solid fa-circle-check" id="tick-box-3"  v-if="CorrectKeywordThree && KeywordThree"></i>
          <i
          id="cross-3"
          class="fa-solid fa-circle-xmark"
          v-if="!CorrectKeywordThree && KeywordThree"
        ></i>
          <input type="text" class="keyword-box" id="fourthbox" v-model="KeywordFour"><i class="fa-solid fa-circle-check" id="tick-box-4" v-if="CorrectKeywordFour&& KeywordFour"></i>
          <i
          id="cross-4"
          class="fa-solid fa-circle-xmark"
          v-if="!CorrectKeywordFour && KeywordFour"
        ></i>
        </div>
        <div class="row-two">
          <input type="text" class="keyword-box" id="firstbox2" v-model="KeywordOneOne"><i class="fa-solid fa-circle-check" id="tick-box-5"  v-if="CorrectKeywordOneTwo && KeywordOneOne"></i>
          <i
          id="cross-5"
          class="fa-solid fa-circle-xmark"
          v-if="!CorrectKeywordOneOne && KeywordOneOne"
        ></i>
          <input type="text" class="keyword-box" id="secondbox2" v-model="KeywordOneTwo"><i class="fa-solid fa-circle-check" id="tick-box-6"  v-if="CorrectKeywordOneTwo && KeywordOneTwo"></i>
          <i
          id="cross-6"
          class="fa-solid fa-circle-xmark"
          v-if="!CorrectKeywordOneTwo && KeywordOneTwo"
        ></i>
          <input type="text" class="keyword-box" id="thirdbox2" v-model="KeywordOneThree"><i class="fa-solid fa-circle-check" id="tick-box-7" v-if="CorrectKeywordOneThree && KeywordOneThree"></i>
          <i
          id="cross-7"
          class="fa-solid fa-circle-xmark"
          v-if="!CorrectKeywordOneThree && KeywordOneThree"
        ></i>
          <input type="text" class="keyword-box" id="fourthbox2" v-model="KeywordOneFour"><i class="fa-solid fa-circle-check" id="tick-box-8"  v-if="CorrectKeywordOneFour && KeywordOneFour"></i>
          <i
          id="cross-8"
          class="fa-solid fa-circle-xmark"
          v-if="!CorrectKeywordOneFour && KeywordOneFour"
        ></i>
        </div>-->
          <div class="keyword-row">
            <div
              v-for="(keyword, index) in firstRowKeywords"
              :key="index"
              class="keyword-box"
            >
              <input
                type="text"
                v-model="keyword.value"
                @input="checkDuplicate(keyword, index, 'firstRowKeywords')"
              />
              <i v-if="keyword.value && !keyword.duplicate" class="fa-solid fa-circle-check valid"></i>
              <i v-else-if="keyword.value && keyword.duplicate" class="fa-solid fa-circle-xmark invalid"></i>
            </div>
          </div>
          <div class="keyword-row">
            <div
              v-for="(keyword, index) in secondRowKeywords"
              :key="index"
              class="keyword-box"
            >
              <input
                type="text"
                v-model="keyword.value"
                @input="checkDuplicate(keyword, index, 'secondRowKeywords')"
              />
              <i v-if="keyword.value && !keyword.duplicate" class="fa-solid fa-circle-check valid"></i>
              <i v-else-if="keyword.value && keyword.duplicate" class="fa-solid fa-circle-xmark invalid"></i>
            </div>
          </div>
        </div>
      </div>
      <div class="access-constraints">
        <label for="ac-cs" class="ac-cs">Access Constraints</label><br />
        <input type="text" id="ac-cs" v-model="AccessConstraint" @input="ValidateAccessConstraints"/>
        <i
          class="fa-solid fa-circle-check"
          id="tick-ac-cs"
          v-if="CorrectAccessConstraints && AccessConstraint"
        ></i>
        <i
          id="cross-ac-cs"
          class="fa-solid fa-circle-xmark"
          v-if="!CorrectAccessConstraints && AccessConstraint"
        ></i>
      </div>
      <div class="use-constraints">
        <label for="use-cs" class="use-cs">Use-Constraints</label> <br />
        <input type="text" id="use-cs" v-model="UseConstraints" @input="ValidateUseConstraints"/><i
          class="fa-solid fa-circle-check"
          id="tick-use-cs"
          v-if="CorrectUseConstraints && UseConstraints"
        ></i>
        <i
          id="cross-use-cs"
          class="fa-solid fa-circle-xmark"
          v-if="!CorrectUseConstraints && UseConstraints"
        ></i>
      </div>
      <div class="purpose">
        <label for="purpose" class="heading-purpose"
          >Purpose of creating data</label
        ><br />
        <input type="text" id="purpose" v-model="Purpose" @input="ValidatePurpose" /><i
          class="fa-solid fa-circle-check"
          id="tick-purpose"
          v-if="CorrectPurpose && Purpose"
        ></i>
        <i
          id="cross-purpose"
          class="fa-solid fa-circle-xmark"
          v-if="!CorrectPurpose && Purpose"
        ></i>
      </div>
      <div class="bottom">
        <div class="data-type">
          <label for="dataType">Data Type</label><br />
          <select name="data-type" id="dataType" v-model="dataType">
            <option value="Vector_Data">Vector Data</option>
            <option value="Raster_Data">Raster Data</option>
          </select>
        </div>
        <div class="Edition">
          <label for="edition">Edition</label><br />
          <select name="edition" id="edition" v-model="edition">
            <option value="first">First</option>
            <option value="second">Second</option>
          </select>
        </div>
        <div class="Status">
          <label for="status">Status</label><br />
          <select name="status" id="status" v-model="status">
            <option value="completed">Completed</option>
            <option value="in progress">In Progress</option>
          </select>
        </div>
      </div>
    </div>
    <div class="bottom-layer">
    <div class="steps">
      <span id="current-step">2</span> of <span id="total-steps">12</span>
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
import { ref, watch } from "vue";
import useValidate from "@vuelidate/core";

export default {
  props: ["subtheme", "theme"],
  setup(props, { emit }) {
    
    const CorrectNameOfDataset = ref(true);
    const firstRowKeywords = ref([
      { value: "", duplicate: false },
      { value: "", duplicate: false },
      { value: "", duplicate: false },
      { value: "", duplicate: false },
    ]);

    const secondRowKeywords = ref([
      { value: "", duplicate: false },
      { value: "", duplicate: false },
      { value: "", duplicate: false },
      { value: "", duplicate: false },
    ]);

    // const CorrectTheme = ref(true);
  
    // const CorrectKeywordOne = ref(false);
    // const KeywordOne = ref("");
    // const CorrectKeywordTwo = ref(true);
    // const KeywordTwo = ref("");
    // const CorrectKeywordThree = ref(true);
    // const KeywordThree = ref("");
    // const CorrectKeywordFour = ref(true);
    // const KeywordFour = ref("");
    // const CorrectKeywordOneOne = ref(true);
    // const KeywordOneOne = ref("");
    // const CorrectKeywordOneTwo = ref(true);
    // const KeywordOneTwo = ref("");
    // const CorrectKeywordOneThree = ref(true);
    // const KeywordOneThree = ref("");
    // const CorrectKeywordOneFour = ref(true);
    // const KeywordOneFour = ref("");
    const status = ref("");
    const edition = ref("");
    const dataType = ref("");
    const CorrectAccessConstraints = ref(false);
    const AccessConstraint = ref("");
    const v$ = useValidate();
    const CorrectUseConstraints = ref(false);
    const UseConstraints = ref("");
    const CorrectPurpose = ref(false);
    const Purpose = ref("");

    const handleRightClick = () => {
      // const { emit } = getCurrentInstance(); // Access emit function using getCurrentInstance
      // Emit an event to the parent component to validate and proceed
      // Ensure that the necessary data is filled
     
        // Emit an event to the parent component
        // This event is caught in the parent component to proceed to the next step

        const data = {
        
        AccessConstraint: AccessConstraint.value,
        CorrectAccessConstraints: CorrectAccessConstraints.value,
        UseConstraints: UseConstraints.value,
        CorrectUseConstraints: CorrectUseConstraints.value,
        Purpose: Purpose.value,
        CorrectPurpose: CorrectPurpose.value,
        firstRowKeywords: firstRowKeywords.value,
        secondRowKeywords: secondRowKeywords.value,
        dataType: dataType.value,
        edition: edition.value,
        status: status.value,
        
        
      };
      // Emit the 'update-data' event with the updated data
      emit("update-data", data);

        emit('validate-and-proceed-second-form');
        console.log('emiteed');
       
      
    };
    
    const handleLeftClick = () =>{
      emit('MoveBackToExtra')
    }

    //Check Access COnstraint Length is < 100
    const ValidateAccessConstraints= ()=>{
      CorrectAccessConstraints.value = AccessConstraint.value.length < 100;
    } 

    // Watch for changes in AccessConstraint
    watch(AccessConstraint, () => {
      ValidateAccessConstraints();
    });
    

    //Check USe COnstraint Length is < 100
    const ValidateUseConstraints= ()=>{
      CorrectUseConstraints.value = UseConstraints.value.length < 100;
    } 
    
    // Watch for changes in USeConstraint
    watch(UseConstraints, () => {
      ValidateUseConstraints();
    });

    //Check Access COnstraint Length is < 100
    const ValidatePurpose= ()=>{
      CorrectPurpose.value = Purpose.value.length < 200;
    } 

    // Watch for changes in AccessConstraint
    watch(AccessConstraint, () => {
      ValidateAccessConstraints();
    });
   

    // Function to check for duplicate keywords
    const checkDuplicate = (keyword, rowIndex, rowType) => {
      if (!keyword.value) {
    keyword.duplicate = false; // Reset duplicate flag if input is empty
    return;

    
  }

  const rowKeywords = rowType === 'firstRowKeywords' ? firstRowKeywords.value : secondRowKeywords.value;
  const allKeywords = [...firstRowKeywords.value, ...secondRowKeywords.value];
  const allValues = allKeywords.map(item => item.value.toLowerCase());

  const currentIndex = rowIndex + (rowType === 'secondRowKeywords' ? firstRowKeywords.value.length : 0);
  const currentValue = keyword.value.toLowerCase();
  const isDuplicate = allValues.filter((item, index) => index !== currentIndex && item === currentValue).length > 0;

  keyword.duplicate = isDuplicate;

  // Check for duplicates across both rows
  if (isDuplicate) {
    alert('Keywords must be different.');
  }
    };

    // Return variables to be used in the component
    return {
      
      ValidateAccessConstraints,
      ValidatePurpose,
      checkDuplicate,
      handleLeftClick,
      secondRowKeywords,
      firstRowKeywords,
      CorrectAccessConstraints,
      CorrectUseConstraints,
      CorrectPurpose,
      Purpose,
      AccessConstraint,
      UseConstraints,
      v$,
      status,
      edition,
      dataType,
      handleRightClick, 
    };
  },
};
</script>


<style scoped>
i {
  z-index: 999;
}

body {
  padding: 0;
  margin: 0;
}

.bottom {
  display: flex;
  /* align-items: center; */
  justify-content: space-evenly;
  gap: 82px;
}

#cross-nom {
  color: crimson;
  position: relative;
  right: 190px;
}
#cross-theme {
  color: crimson;
  position: relative;
  right: 105px;
}

.keyword-rows {
  display: flex;
  flex-direction: column;
}

.keyword-row {
  display: flex;
  justify-content: space-between;
}

.keyword-box {
  width: calc(25% - 10px); /* Adjust as needed */
  position: relative;
}

.keyword-box input {
  width: 100%;
}

/* Add styles for valid and invalid icons */
.valid {
  color: green;
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  right: 10px;
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


.invalid {
  color: crimson;
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  right: 10px;
}

#tick-theme {
  color: green;
  position: relative;
  right: 105px;
}

#tick-nom {
  color: green;
  position: relative;
  right: 190px;
}

#tick-box-1,
#tick-box-5 {
  color: green;
  position: absolute;
  top: 15px;
  left: 125px;
}
#tick-box-2,
#tick-box-6 {
  color: green;
  position: absolute;
  top: 15px;
  left: 273px;
}
#tick-box-3,
#tick-box-7 {
  color: green;
  position: absolute;
  top: 15px;
  left: 419px;
}
#tick-box-4,
#tick-box-8 {
  color: green;
  position: absolute;
  top: 15px;
  left: 561px;
}

#tick-purpose,
#tick-use-cs,
#tick-ac-cs {
  color: green;
  position: relative;
  right: 37px;
}

#right {
  transform: rotate(180deg);
  position: relative;
  left: 5px;
}

#cross-1,
#cross-5 {
  color: crimson;
  position: absolute;
  top: 15px;
  left: 125px;
}
#cross-2,
#cross-6 {
  color: crimson;
  position: absolute;
  top: 15px;
  left: 273px;
}
#cross-3,
#cross-7 {
  color: crimson;
  position: absolute;
  top: 15px;
  left: 419px;
}
#cross-4,
#cross-8 {
  color: crimson;
  position: absolute;
  top: 15px;
  left: 561px;
}

#cross-purpose,
#cross-use-cs,
#cross-ac-cs {
  color: crimson;
  position: relative;
  right: 37px;
}

h1 {
  margin: 0;
}
.form-container-two {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  margin-bottom: 100px;
}

.white-container {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: 10px;

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
  padding: 35px 27px 37px 25px;
  max-width: 100%;
}

.nom {
  position: relative;
  right: 220px;
}

.heading {
  position: relative;
  right: 163px;
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

.themelabel {
  position: relative;
  right: 260px;
}

.keyword-heading {
  position: relative;
  right: 250px;
}

.ac-cs {
  position: relative;
  right: 217px;
}

.use-cs {
  position: relative;
  right: 227px;
}

.heading-purpose {
  position: relative;
  right: 194px;
}
.name-of-dataset input {
  position: relative;
  right: 164px;
  width: 257px; /* Adjust as needed */
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

.theme input {
  position: relative;
  right: 75px;
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

.boxes {
  display: flex;
  flex-direction: column;
  gap: 5px;
}

.row-one {
  position: relative;
  right: 16px;
}
.row-two {
  position: relative;
  right: 16px;
}

.keywords input {
  width: 130px; /* Adjust as needed */
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
  margin-left: 14px;
}
.access-constraints input {
  width: 567px; /* Adjust as needed */
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
  position: relative;
  right: 11px;
}

.use-constraints input {
  width: 567px; /* Adjust as needed */
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
  position: relative;
  right: 11px;
}
.purpose input {
  width: 567px; /* Adjust as needed */
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
  position: relative;
  right: 11px;
}
.data-type select {
  width: 137px; /* Adjust as needed */
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

.Edition select {
  width: 137px; /* Adjust as needed */
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

.Status select {
  width: 137px; /* Adjust as needed */
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

input,
select {
  margin-top: 5px;
}
</style>