<template>
  <div class="pdm-container">
    <div class="top-container">
      <div class="logo">
        <img src="../assets/vedas.png" alt="vedas logo" />
      </div>
      <div class="user">
        <img class="user-button" src="../assets/userbg.png" alt="user-image" />
      </div>
    </div>
    <div class="mid-container">
      <div class="heading">
        <h1>Primary Data Mangement</h1>
      </div>
      <div class="back">
        <button @click="$router.push('/primary-data-main-page')">
          <i class="fa-solid fa-arrow-left" id="back-arrow"></i>
          <p class="text-back">Back</p>
        </button>
      </div>
      <form @submit.prevent="submitForm" class="form-containers">
        <transition name="slide-fade">
          <div class="form-container-1" v-show="showFormContainerOne">
            <FormContainerOne
              :subtheme="subtheme"
              :theme="theme"
              :BasePath="BasePath"
              @update-data="handleUpdateDataOne"
              @validate-and-proceed="ExtraFormHandleValidationAndProceed"
            />
          </div>
        </transition>

        <transition name="extra-form-slide-fade">
          <div class="extra-cont" v-show="showExtraFormContainer">
            <ExtraFormContainer
              ref="formContainerOne"
              :subtheme="subtheme"
              :theme="theme"
              @update-data="handleUpdateDataExtra"
              @validate-and-proceed="handleValidationAndProceed"
              @MoveBackToOne="handleMoveBackToOne"
            />
          </div>
        </transition>

        <div class="form-container-2">
          <FormContainerTwo
            v-show="showFormContainerTwo"
            :theme="theme"
            :subtheme="subtheme"
            @update-data="handleUpdateDataTwo"
            @validate-and-proceed-second-form="
              FormTwoHandleValidationAndProceed
            "
            @MoveBackToExtra="handleMoveBackToExtra"
          />
        </div>
        <div class="form-container-3">
          <FormContainerThree
            v-show="showFormContainerThree"
            @validate-and-proceed-form-three="
              FormThreeHandleValidationAndProceed
            "
            @update-data="handleUpdateDataThree"
            @MoveBackToTwo="handleMoveBackToTwo"
          />
        </div>
        <div class="form-container-4">
          <FormContainerFour
            v-show="showFormContainerFour"
            @validate-and-proceed-form-four="FormFourHandleValidationAndProceed"
            @update-data="handleUpdateDataFour"
            @MoveBackToThree="handleMoveBackToThree"
          />
        </div>
        <div class="form-container-5">
          <FormContainerFive
            v-show="showFormContainerFive"
            @validate-and-proceed-form-five="FormFiveHandleValidationAndProceed"
            @update-data="handleUpdateDataFive"
            @MoveBackToFour="handleMoveBackToFour"
          />
        </div>
        <div class="form-container-6">
          <FormContainerSix
            v-show="showFormContainerSix"
            @update-data="handleUpdateDataSix"
            @validate-and-proceed-form-six="FormSixHandleValidationAndProceed"
            @MoveBackToFive="handleMoveBackToFive"
          />
        </div>
        <div class="form-container-7">
          <FormContainerSeven
            v-show="showFormContainerSeven"
            @validate-and-proceed-form-seven="
              FormSevenHandleValidationAndProceed
            "
            @update-data="handleUpdateDataSeven"
            @MoveBackToSix="handleMoveBackToSix"
          />
        </div>
        <div class="form-container-8">
          <FormContainerEight
            v-show="showFormContainerEight"
            @validate-and-proceed-form-eight="
              FormEightHandleValidationAndProceed
            "
            @update-data="handleUpdateDataEight"
            @MoveBackToSeven="handleMoveBackToSeven"
          />
        </div>
        <div class="form-container-9">
          <FormContainerNine
            v-show="showFormContainerNine"
            @update-data="handleUpdateDataNine"
            @validate-and-proceed-form-nine="FormNineHandleValidationAndProceed"
            @MoveBackToEight="handleMoveBackToEight"
          />
        </div>
        <div class="form-container-10">
          <FormContainerTen
            v-show="showFormContainerTen"
            @update-data="handleUpdateDataTen"
            @validate-and-proceed-form-ten="FormTenHandleValidationAndProceed"
            @MoveBackToNine="handleMoveBackToNine"
          />
        </div>
        <div class="form-container-11">
          <FormContainerEleven
            v-show="showFormContainerEleven"
            @update-data="handleUpdateDataEleven"
            @MoveBackToTen="handleMoveBackToTen"
          />
          <div class="submit-button" v-show="showFormContainerEleven">
            <button type="submit">Submit</button>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import FormContainerOne from "../components/FormContainerOne.vue";
import ExtraFormContainer from "../components/ExtraFormContainer.vue";
import FormContainerTwo from "../components/FormContainerTwo.vue";
import FormContainerThree from "../components/FormContainerThree.vue";
import FormContainerFour from "../components/FormContainerFour.vue";
import FormContainerFive from "../components/FormContainerFive.vue";
import FormContainerSix from "../components/FormContainerSix.vue";
import FormContainerSeven from "../components/FormContainerSeven.vue";
import FormContainerEight from "../components/FormContainerEight.vue";
import FormContainerNine from "../components/FormContainerNine.vue";
import FormContainerTen from "../components/FormContainerTen.vue";
import FormContainerEleven from "../components/FormContainerEleven.vue";

export default {
  data() {
    return {
      showFormContainerOne: true,
      showFormContainerTwo: false,
      showExtraFormContainer: false,
      showFormContainerThree: false,
      showFormContainerFour: false,
      showFormContainerFive: false,
      showFormContainerSix: false,
      showFormContainerSeven: false,
      showFormContainerEight: false,
      showFormContainerNine: false,
      showFormContainerTen: false,
      showFormContainerEleven: false,
      theme: "",
      subtheme: "",
      BasePath: "",
      Projection: "",
      extension: "",
      Compression: "",
      Projection2: "",
      Projection3: "",
      CorrectProjectOne: "",
      CorrectProjectTwo: "",
      CorrectProjectThree: "",
      Sampling: "",
      formCompleted: false,
    };
  },
  name: "primary-data-management",
  components: {
    FormContainerOne,
    ExtraFormContainer,
    FormContainerTwo,
    FormContainerThree,
    FormContainerFour,
    FormContainerFive,
    FormContainerSix,
    FormContainerSeven,
    FormContainerEight,
    FormContainerNine,
    FormContainerTen,
    FormContainerEleven,
  },
  methods: {
    handleMoveBackToOne() {
      this.showFormContainerOne = true;
      this.showExtraFormContainer = false;
    },

    handleMoveBackToExtra() {
      this.showExtraFormContainer = true;
      this.showFormContainerTwo = false;
    },
    handleMoveBackToTwo() {
      this.showFormContainerTwo = true;
      this.showFormContainerThree = false;
    },
    handleMoveBackToThree() {
      this.showFormContainerThree = true;
      this.showFormContainerFour = false;
    },
    handleMoveBackToFour() {
      this.showFormContainerFour = true;
      this.showFormContainerFive = false;
    },
    handleMoveBackToFive() {
      this.showFormContainerFive = true;
      this.showFormContainerSix = false;
    },
    handleMoveBackToSix() {
      this.showFormContainerSix = true;
      this.showFormContainerSeven = false;
    },
    handleMoveBackToSeven() {
      this.showFormContainerSeven = true;
      this.showFormContainerEight = false;
    },
    handleMoveBackToEight() {
      this.showFormContainerEight = true;
      this.showFormContainerNine = false;
    },
    handleMoveBackToNine() {
      this.showFormContainerNine = true;
      this.showFormContainerTen = false;
    },
    handleMoveBackToTen() {
      this.showFormContainerTen = true;
      this.showFormContainerEleven = false;
    },

    ExtraFormHandleValidationAndProceed() {
      this.showFormContainerOne = false;
      this.showExtraFormContainer = true;
    },
    handleValidationAndProceed(subtheme, theme, data) {
      console.log(data);

      console.log("Theme value:", theme);
      this.subtheme = subtheme;
      this.theme = theme; // Set the value of theme here
      this.showExtraFormContainer = false;
      this.showFormContainerTwo = true;
    },
    FormTwoHandleValidationAndProceed() {
      this.showFormContainerTwo = false;
      this.showFormContainerThree = true;
    },
    FormThreeHandleValidationAndProceed() {
      this.showFormContainerThree = false;
      this.showFormContainerFour = true;
    },
    FormFourHandleValidationAndProceed() {
      this.showFormContainerFour = false;
      this.showFormContainerFive = true;
    },
    FormFiveHandleValidationAndProceed() {
      this.showFormContainerFive = false;
      this.showFormContainerSix = true;
    },
    FormSixHandleValidationAndProceed() {
      this.showFormContainerSix = false;
      this.showFormContainerSeven = true;
    },
    FormSevenHandleValidationAndProceed() {
      this.showFormContainerSeven = false;
      this.showFormContainerEight = true;
    },
    FormEightHandleValidationAndProceed() {
      this.showFormContainerEight = false;
      this.showFormContainerNine = true;
    },
    FormNineHandleValidationAndProceed() {
      this.showFormContainerNine = false;
      this.showFormContainerTen = true;
    },
    FormTenHandleValidationAndProceed() {
      this.showFormContainerTen = false;
      this.showFormContainerEleven = true;
    },
    handleUpdateDataOne(data) {
      this.subtheme = data.subtheme;
      this.theme = data.theme;
      this.BasePath = data.BasePath;
    },
    handleUpdateDataExtra(data) {
      // Update your data properties with the emitted data from the child component

      this.extension = data.extension;
      this.Compression = data.Compression;
      this.Projection = data.Projection;
      this.Projection2 = data.Projection2;
      this.Projection3 = data.Projection3;
      this.CorrectProjectOne = data.CorrectProjectOne;
      this.CorrectProjectTwo = data.CorrectProjectTwo;
      this.CorrectProjectThree = data.CorrectProjectThree;
      this.Sampling = data.Sampling;
    },
    handleUpdateDataTwo(data) {
      // Update your data properties with the emitted data from the child component

      this.status = data.status;
      this.edition = data.edition;
      this.dataType = data.dataType;
      this.AccessConstraint = data.AccessConstraint;
      this.CorrectAccessConstraints = data.CorrectAccessConstraints;
      this.UseConstraints = data.UseConstraints;
      this.CorrectUseConstraints = data.CorrectUseConstraints;
      this.Purpose = data.Purpose;
      this.CorrectPurpose = data.CorrectPurpose;
      this.firstRowKeywords = data.firstRowKeywords;
      this.secondRowKeywords = data.secondRowKeywords;
    },
    handleUpdateDataThree(data) {
      // Update your data properties with the emitted data from the child component
      this.city = data.city;
      this.country = data.country;
      this.ContactPerson = data.ContactPerson;
      this.CorrectContactPerson = data.CorrectContactPerson;
      this.ContactTelephone = data.ContactTelephone;
      this.CorrectContactTelephone = data.CorrectContactTelephone;
      this.organization = data.organization;
      this.CorrectOrganization = data.CorrectOrganization;
      this.MailAddress = data.MailAddress;
      this.CorrectMailAddress = data.CorrectMailAddress;
      this.CorrectFaxNumber = data.CorrectFaxNumber;
      this.FaxNumber = data.FaxNumber;
    },
    handleUpdateDataFour(data) {
      // Update your data properties with the emitted data from the child component

      this.datum = data.datum;
      this.spheroid = data.spheroid;
      this.CorrectSpheroid = data.CorrectSpheroid;
      this.CorrectDatum = data.CorrectDatum;
    },
    handleUpdateDataFive(data) {
      // Update your data properties with the emitted data from the child component

      this.yLl = data.yLl;
      this.CorrectYLl = data.CorrectYLl;
      this.xLl = data.xLl;
      this.CorrectXLl = data.CorrectXLl;
      this.yLr = data.yLr;
      this.CorrectYlr = data.CorrectYlr;
      this.xLr = data.xLr;
      this.CorrectXlr = data.CorrectXlr;
      this.xUl = data.xUl;
      this.CorrectXUl = data.CorrectXUl;
      this.yUl = data.yUl;
      this.CorrectYUl = data.CorrectYUl;
      this.xUr = data.xUr;
      this.CorrectXUr = data.CorrectXUr;
      this.yUr = data.yUr;
      this.CorrectYUr = data.CorrectYUr;
    },

    handleUpdateDataSix(data) {
      // Update your data properties with the emitted data from the child component
      this.date = data.date;
    },

    handleUpdateDataSeven(data) {
      this.dpb = data.dpb;
      this.Correctdpb = data.Correctdpb;
      this.ogsc = data.ogsc;
      this.CorrectOgsc = data.CorrectOgsc;
      this.CorrectSourceScale = data.CorrectSourceScale;
      this.SourceScale = data.SourceScale;
      this.SourceDate = data.SourceDate;
      this.Lineage = data.Lineage;
      this.CorrectLineage = data.CorrectLineage;
      this.cn = data.cn;
      this.CorrectCn = data.CorrectCn;
      this.ad = data.ad;
      this.CorrectAd = data.CorrectAd;
    },

    handleUpdateDataEight(data) {
      // Update your data properties with the emitted data from the child component
      this.DITC = data.DITC;
    },
    handleUpdateDataNine(data) {
      // Update your data properties with the emitted data from the child component
      this.language = data.language;
      this.Correctlanguage = data.Correctlanguage;
    },
    handleUpdateDataTen(data) {
      // Update your data properties with the emitted data from the child component
      this.dia = data.dia;
      this.CorrectDia = data.CorrectDia;
    },
    handleUpdateDataEleven(data) {
      // Update your data properties with the emitted data from the child component
      this.pd = data.pd;
      this.Correctpd = data.Correctpd;
      this.accReport = data.accReport;
      this.CorrectAccR = data.CorrectAccR;
      this.horpor = data.horpor;
      this.Correcthorpor = data.Correcthorpor;
    },

    submitForm() {
      console.log(
        "pd:",
        this.pd,
        "Correctpd:",
        this.Correctpd,
        "accReport:",
        this.accReport,
        "CorrectAccR:",
        this.CorrectAccR,
        "horpor:",
        this.horpor,
        "Correcthorpor:",
        this.Correcthorpor,
        "DITC:",
        this.DITC,
        "dpb:",
        this.dpb,
        "Correctdpb:",
        this.Correctdpb,
        "ogsc:",
        this.ogsc,
        "CorrectOgsc:",
        this.CorrectOgsc,
        "CorrectSourceScale:",
        this.CorrectSourceScale,
        "SourceScale:",
        this.SourceScale,
        "SourceDate:",
        this.SourceDate,
        "Lineage:",
        this.Lineage,
        "CorrectLineage:",
        this.CorrectLineage,
        "cn:",
        this.cn,
        "CorrectCn:",
        this.CorrectCn,
        "ad:",
        this.ad,
        "CorrectAd:",
        this.CorrectAd,
        "date:",
        this.date,
        "yLl:",
        this.yLl,
        "CorrectYLl:",
        this.CorrectYLl,
        "xLl:",
        this.xLl,
        "CorrectXLl:",
        this.CorrectXLl,
        "yLr:",
        this.yLr,
        "CorrectYlr:",
        this.CorrectYlr,
        "xLr:",
        this.xLr,
        "CorrectXlr:",
        this.CorrectXlr,
        "xUl:",
        this.xUl,
        "CorrectXUl:",
        this.CorrectXUl,
        "yUl:",
        this.yUl,
        "CorrectYUl:",
        this.CorrectYUl,
        "xUr:",
        this.xUr,
        "CorrectXUr:",
        this.CorrectXUr,
        "yUr:",
        this.yUr,
        "CorrectYUr:",
        this.CorrectYUr,
        "BasePath:",
        this.BasePath,
        "subtheme:",
        this.subtheme,
        "Projection:",
        this.Projection,
        "extension:",
        this.extension,
        "Compression:",
        this.Compression,
        "Projection2:",
        this.Projection2,
        "Projection3:",
        this.Projection3,
        "CorrectProjectOne:",
        this.CorrectProjectOne,
        "CorrectProjectTwo:",
        this.CorrectProjectTwo,
        "CorrectProjectThree:",
        this.CorrectProjectThree,
        "city:",
        this.city,
        "country:",
        this.country,
        "ContactPerson:",
        this.ContactPerson,
        "CorrectContactPerson:",
        this.CorrectContactPerson,
        "ContactTelephone:",
        this.ContactTelephone,
        "CorrectContactTelephone:",
        this.CorrectContactTelephone,
        "organization:",
        this.organization,
        "CorrectOrganization:",
        this.CorrectOrganization,
        "MailAddress:",
        this.MailAddress,
        "CorrectMailAddress:",
        this.CorrectMailAddress,
        "FaxNumber:",
        this.FaxNumber,
        "status:",
        this.status,
        "edition:",
        this.edition,
        "dataType:",
        this.dataType,
        "AccessConstraint:",
        this.AccessConstraint,
        "CorrectAccessConstraints:",
        this.CorrectAccessConstraints,
        "UseConstraints:",
        this.UseConstraints,
        "CorrectUseConstraints:",
        this.CorrectUseConstraints,
        "Purpose:",
        this.Purpose,
        "CorrectPurpose:",
        this.CorrectPurpose,
        "firstRowKeywords:",
        this.firstRowKeywords,
        "secondRowKeywords:",
        this.secondRowKeywords,
        "datum:",
        this.datum,
        "spheroid:",
        this.spheroid,
        "CorrectSpheroid:",
        this.CorrectSpheroid,
        "CorrectDatum:",
        this.CorrectDatum
      );
      // Check if all data properties are populated
      if (
        this.pd &&
        this.Correctpd &&
        this.accReport &&
        this.CorrectAccR &&
        this.horpor &&
        this.Correcthorpor &&
        this.DITC &&
        this.dpb &&
        this.Correctdpb &&
        this.ogsc &&
        this.CorrectOgsc &&
        this.CorrectSourceScale &&
        this.SourceScale &&
        this.SourceDate &&
        this.Lineage &&
        this.CorrectLineage &&
        this.cn &&
        this.CorrectCn &&
        this.ad &&
        this.CorrectAd &&
        this.date &&
        this.yLl &&
        this.CorrectYLl &&
        this.xLl &&
        this.CorrectXLl &&
        this.yLr &&
        this.CorrectYlr &&
        this.xLr &&
        this.CorrectXlr &&
        this.xUl &&
        this.CorrectXUl &&
        this.yUl &&
        this.CorrectYUl &&
        this.xUr &&
        this.CorrectXUr &&
        this.yUr &&
        this.CorrectYUr &&
        this.BasePath &&
        this.subtheme &&
        this.Projection &&
        this.extension &&
        this.Compression &&
        this.Projection2 &&
        this.Projection3 &&
        this.CorrectProjectOne &&
        this.CorrectProjectTwo &&
        this.CorrectProjectThree &&
        this.city &&
        this.country &&
        this.ContactPerson &&
        this.CorrectContactPerson &&
        this.ContactTelephone &&
        this.CorrectContactTelephone &&
        this.organization &&
        this.CorrectOrganization &&
        this.MailAddress &&
        this.CorrectMailAddress &&
        this.FaxNumber &&
        this.status &&
        this.edition &&
        this.dataType &&
        this.AccessConstraint &&
        this.CorrectAccessConstraints &&
        this.UseConstraints &&
        this.CorrectUseConstraints &&
        this.Purpose &&
        this.CorrectPurpose &&
        this.firstRowKeywords &&
        this.secondRowKeywords &&
        this.datum &&
        this.spheroid &&
        this.CorrectSpheroid &&
        this.CorrectDatum
      ) {
        // All data is entered, proceed with form submission

        alert("All data entered. Proceeding with form submission...");
        // You can submit the form here
      } else {
        // Data is incomplete, show error message to the user

        alert("Please fill in all the required fields.");
        // You can also display an error message to the user
      }
    },
  },
};
</script>
<style scoped>
body,
html {
  margin: 0;
  padding: 0;
  height: 100%;
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

.submit-button button {
  display: flex;
  justify-content: center;
  align-items: center;
}

.submit-button {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  right: 35px;
}

#back-arrow {
  position: relative;
  top: 18px;
  left: 18px;
  font-size: 22px;
}
.top-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  padding: 0;
  background: inherit;
  display: flex;
  justify-content: space-between;
}

.logo {
  margin-right: 20px; /* Add some spacing between the logo and other content */
  position: fixed;
}

.logo img {
  margin-left: 20px;
}

.user-button {
  width: 80px;
  margin: 33px;
  border-radius: 50%; /* Add rounded corners */
  box-shadow: 0px 1px 5px rgb(94, 77, 77);
  position: fixed;
  right: 0;
}

.form-container-6 {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.user-button:hover {
  box-shadow: 0px 0px 0px rgb(94, 77, 77);
  cursor: pointer;
  z-index: 20;
}

.user-button {
  --clr-font-main: hsla(0 0% 20% / 100);
  --btn-bg-1: rgb(65, 145, 249);
  --btn-bg-2: hsla(194 100% 56% / 1);
  --btn-bg-color: hsla(360 100% 100% / 1);
  --radii: 0.5em;
  cursor: pointer;
  min-width: 120px;

  font-size: var(--size, 1rem);
  font-family: "Segoe UI", system-ui, sans-serif;
  font-weight: 500;
  transition: 0.8s;
  background-size: 280% auto;
  border: none;
  width: 50px;
  border-radius: 50%;
  color: var(--btn-bg-color);
  box-shadow: 0px 0px 20px rgba(71, 184, 255, 0.5),
    0px 5px 5px -1px rgba(58, 125, 233, 0.25),
    inset 4px 4px 8px rgba(175, 230, 255, 0.5),
    inset -4px -4px 8px rgba(19, 95, 216, 0.35);
}

.user-button:hover {
  background-position: right top;
}

.user-button:is(:focus, :focus-visible, :active) {
  outline: none;
  box-shadow: 0 0 0 3px var(--btn-bg-color), 0 0 0 6px var(--btn-bg-2);
}

@media (prefers-reduced-motion: reduce) {
  .user-button {
    transition: linear;
  }
}

.pdm-container {
  padding-top: 130px;
  display: flex;
  justify-content: center;
  align-items: stretch;
  height: 150vh;
  width: 100%;
  background: linear-gradient(
    to right,
    #c3e5f9,
    #bae1f6,
    #b0dcf3,
    #a6d8f0,
    #9cd4ed,
    #93d1eb,
    #89cde8,
    #7fcae6,
    #73c6e4,
    #67c2e3,
    #59bee1,
    #49bae0
  ); /* Gradient background */
}

button img {
  width: 30px;
  margin-top: 5px;
}

.form-containers {
  display: flex;
  /* Allow containers to wrap to the next line */
  justify-content: flex-start; /* Align containers to the start of the line */
  position: relative;
  justify-content: space-between;
}

.text-back {
  position: relative;
  top: 0.7px;
  right: 20px;
  font-size: 16px;
}

.back button {
  left: 20%;
}

button {
  display: flex;
  justify-content: space-between;
  width: 90px;
  margin: 33px;
  border-radius: 50px; /* Add rounded corners */
  box-shadow: 0px 1px 5px rgb(94, 77, 77);
  margin-bottom: 20px;
  margin-top: 20px;
  position: relative;
}

.form-containers {
  display: flex;
  position: relative;
  justify-content: center;
  align-items: center;
  left: 23%;
}

.slide-fade-enter-active,
.slide-fade-leave-active {
  transition: all 0.5s ease;
}

.slide-fade-enter, .slide-fade-leave-to /* .slide-fade-leave-active in <2.1.8 */ {
  opacity: 0;
  transform: translateY(-20px);
}

.extra-form-slide-fade-enter-active,
.extra-form-slide-fade-leave-active {
  transition: all 0.5s ease;
}

.extra-form-slide-fade-enter, .extra-form-slide-fade-leave-to /* .extra-form-slide-fade-leave-active in <2.1.8 */ {
  opacity: 0;
  transform: translateY(
    -20px
  ); /* You can adjust the translateY value as per your preference */
}

.form-container-1,
.form-container-2,
.form-container-3,
.form-container-6,
.form-container-4,
.form-container-5,
.form-container-6,
.form-container-7,
.form-container-8,
.form-container-9,
.form-container-10,
.form-container-11 {
  z-index: 999;
  padding: 15px;
}

.form-container-3 {
  position: relative;
  right: 70px;
}
.form-container-2 {
  position: relative;
  right: 68px;
}

.form-container-1 {
  position: relative;
  right: 68px;
}

.extra-cont {
  position: relative;
  right: 70px;
}

.form-container-4 {
  position: relative;
  right: 68px;
}

.form-container-5 {
  position: relative;
  right: 85px;
}

.form-container-6 {
  position: relative;
  right: 68px;
}
.form-container-7 {
  position: relative;
  right: 214px;
}
.form-container-8 {
  position: relative;
  right: 284px;
}
.form-container-9 {
  position: relative;
  right: 286px;
}
.form-container-10 {
  position: relative;
  right: 293px;
}
.form-container-11 {
  position: relative;
  right: 322px;
}
</style>
