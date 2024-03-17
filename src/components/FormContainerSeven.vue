<template>
  <div class="form-container-seven">
    <div class="white-container">
      <div class="heading">
        <h3>Citation</h3>
      </div>
      <div class="data-prepared-by">
        <label for="dpb" class="dpb-heading">Data Prepared by </label><br />
        <input type="text" id="dpb" v-model="dpb" @input="Validatedpb" />
        <i
          class="fa-solid fa-circle-check"
          id="tick"
          v-if="Correctdpb && dpb"
        ></i>
        <i
          id="cross"
          class="fa-solid fa-circle-xmark"
          v-if="!Correctdpb && dpb"
        ></i>
      </div>
      <div class="original-source">
        <label for="ogsc" class="og">Original Source</label> <br />
        <input type="text" id="ogsc" v-model="ogsc" @input="ValidateOgsc" /><i
          class="fa-solid fa-circle-check"
          id="tick"
          v-if="CorrectOgsc && ogsc"
        ></i>
        <i
          id="tick-ad"
          class="fa-solid fa-circle-check"
          v-if="!CorrectOgsc && ogsc"
        ></i>
      </div>

      <div class="row">
        <div class="source-scale">
          <label for="source-scale">Source Scale</label><br />
          <input type="text" id="source-scale" v-model="SourceScale" @input="ValidateSourceScale"/><i
            class="fa-solid fa-circle-check"
            id="tick-row"
            v-if="CorrectSourceScale && SourceScale"
          ></i>
          <i
            id="cross-row"
            class="fa-solid fa-circle-xmark"
            v-if="!CorrectSourceScale && SourceScale"
          ></i>
        </div>
        <div class="source-date">
          <label for="source-date">Source Date</label><br />
          <input type="date" id="source-date" v-model="SourceDate"/>
        </div>
      </div>

      <div class="Lineage">
        <label for="Lineage" class="heading-Lineage">Lineage</label><br />
        <input
          type="text"
          id="Lineage-input"
          v-model="Lineage"
          @input="ValidateLineage"
        /><i
          class="fa-solid fa-circle-check"
          id="ticklineage"
          v-if="CorrectLineage && Lineage"
        ></i>
        <i
          id="cross"
          class="fa-solid fa-circle-xmark"
          v-if="!CorrectLineage && Lineage"
        ></i>
      </div>
      <div class="coorperate-name">
        <label for="cn" class="heading-cn">Corporate Name</label><br />
        <input type="text" id="cn" v-model="cn" @input="ValidateCn" /><i
          class="fa-solid fa-circle-check"
          id="tickcn"
          v-if="CorrectCn && cn"
        ></i>
        <i
          id="cross"
          class="fa-solid fa-circle-xmark"
          v-if="!CorrectCn && cn"
        ></i>
      </div>
      <div class="coorperate-address">
        <label for="ad" class="heading-ad">Corporate Address</label><br />
        <input type="text" id="ad" v-model="ad" @input="ValidateAd" /><i
          class="fa-solid fa-circle-check"
          id="tickad"
          v-if="CorrectAd && ad"
        ></i>
        <i
          id="cross"
          class="fa-solid fa-circle-xmark"
          v-if="!CorrectAd && ad"
        ></i>
      </div>
    </div>
    <div class="bottom-layer">
      <div class="steps">
        <span id="current-step">7</span> of <span id="total-steps">12</span>
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
  setup(props, { emit }) {
  const dpb = ref("");
  const Correctdpb = ref(false);
   const ogsc = ref("");
  const CorrectOgsc = ref(false);
  const CorrectSourceScale = ref(false);
  const SourceScale = ref("");
  const SourceDate = ref("");
  const Lineage = ref("");
  const CorrectLineage = ref(false);
  const cn = ref("");
  const CorrectCn = ref(false);
  const ad = ref("");
  const CorrectAd = ref(false);
  const v$ = useValidate();

  

  const Validatedpb = () => {
    Correctdpb.value = dpb.value.length < 50 && dpb.value.length > 3;
  };

  watch(dpb, () => {
    Validatedpb();
  });

   const ValidateOgsc = () => {
    CorrectOgsc.value = ogsc.value.length > 3 && ogsc.value.length < 50;
    console.log(CorrectOgsc.value);
  };

  watch(ogsc, () => {
    ValidateOgsc();
  });

  

  const ValidateSourceScale = () => {
    CorrectSourceScale.value = SourceScale.value.length < 100;
  };

  watch(SourceScale, () => {
    ValidateSourceScale();
  });

  const ValidateLineage = () => {
    CorrectLineage.value = Lineage.value.length < 150;
  };

  watch(Lineage, () => {
    ValidateLineage();
  });

  const ValidateCn = () => {
    CorrectCn.value = cn.value.length < 150;
  };

  watch(cn, () => {
    ValidateCn();
  });

  const ValidateAd = () => {
    CorrectAd.value = ad.value.length < 150;
  };

  watch(ad, () => {
    ValidateAd();
  });

const handleLeftClick = () =>{
    emit('MoveBackToSix');
    console.log("emitting donee");
  };
  const handleRightClick = () => {
    console.log("dpb:", dpb.value, "Correctdpb:", Correctdpb.value);
  console.log("ogsc:", ogsc.value, "CorrectOgsc:", CorrectOgsc.value);
  console.log("SourceScale:", SourceScale.value, "CorrectSourceScale:", CorrectSourceScale.value);
  console.log("SourceDate:", SourceDate.value);
  console.log("Lineage:", Lineage.value, "CorrectLineage:", CorrectLineage.value);
  console.log("cn:", cn.value, "CorrectCn:", CorrectCn.value);
  console.log("ad:", ad.value, "CorrectAd:", CorrectAd.value);
    
      const data = {
        dpb: dpb.value,
        Correctdpb: Correctdpb.value,
        ogsc: ogsc.value,
        CorrectOgsc: CorrectOgsc.value,
        CorrectSourceScale: CorrectSourceScale.value,
        SourceScale: SourceScale.value,
        SourceDate: SourceDate.value,
        Lineage: Lineage.value,
        CorrectLineage: CorrectLineage.value,
        cn: cn.value,
        CorrectCn: CorrectCn.value,
        ad: ad.value,
        CorrectAd: CorrectAd.value,
      };

      emit("update-data", data);

      emit('validate-and-proceed-form-seven');  
    
  };

  return {
    Validatedpb,
    dpb,
    Correctdpb,
    ValidateOgsc,
    ogsc,
    CorrectSourceScale,
    SourceScale,
    SourceDate,
    Lineage,
    CorrectLineage,
    CorrectCn,
    CorrectAd,
    ad,
    cn,
    v$,
    handleRightClick,
    handleLeftClick,
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
  top: 332px;
  right: 46px;
  color: green;
}

#tick-og{
  position: absolute;
  top: 322px;
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

.Lineage label {
  right: 210px;
}
</style>
