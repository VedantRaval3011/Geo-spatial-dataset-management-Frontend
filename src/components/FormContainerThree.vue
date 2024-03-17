<template>
  <div class="form-container-three">
    <div class="white-container">
      <div class="heading"><h3>Contact Information</h3></div>
      <div class="row-one">
        <div class="contact-person">
          <label for="contact-person">Contact Person</label><br />
          <div class="contact-person-input">
            <input type="text" id="contact-person" v-model="ContactPerson" @input="ValidateContactPerson"/>
            <i
              class="fa-solid fa-circle-check"
              id="tick-left"
              v-if="CorrectContactPerson && ContactPerson"
            ></i>
            <i
              id="cross-left"
              class="fa-solid fa-circle-xmark"
              v-if="!CorrectContactPerson && ContactPerson"
            ></i>
          </div>
        </div>
        <div class="organization">
          <label for="organization">Organization</label><br />
          <div class="organization-input">
            <input type="text" id="organization" v-model="organization" @input="ValidateOrganization" />
            <i
              class="fa-solid fa-circle-check"
              id="tick-right"
              v-if="CorrectOrganization && organization"
            ></i>
            <i
              id="cross-right"
              class="fa-solid fa-circle-xmark"
              v-if="!CorrectOrganization && organization"
            ></i>
          </div>
        </div>
      </div>
      <div class="row-two">
        <div class="mailing-address">
          <label for="mailing-address">Mailing Address</label><br />
          <div class="mailing-address-input">
            <input type="text" id="mailing-address" v-model="MailAddress" @input="ValidateMailAddress"/>
            <i
              class="fa-solid fa-circle-check"
              id="tick-left"
              v-if="CorrectMailAddress && MailAddress"
            ></i>
            <i
              id="cross-left"
              class="fa-solid fa-circle-xmark"
              v-if="!CorrectMailAddress && MailAddress"
            ></i>
          </div>
        </div>
        <div class="city">
          <label for="city">City/Locality</label><br />
          <select name="city" id="locality" v-model="city">
            <option value="gujarat">Gujarat</option>
            <option value="Delhi">Delhi</option>
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
          </select>
        </div>
      </div>
      <div class="row-three">
        <div class="country">
          <label for="country">Country</label><br />
          <select name="country" id="select-country" v-model="country">
            <option value="india">India</option>
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
          </select>
        </div>
        <div class="contact-telephone">
          <label for="phone">Contact Telephone</label><br />
          <div class="contact-telephone-input" >
            <input type="tel" id="phone" name="phone" pattern="[\d\s()+-]*" v-model="ContactTelephone" @input="ValidateContactTelephone" placeholder="E.g., +1 (555) 123-4567"/>
            <i
              class="fa-solid fa-circle-check"
              id="tick-right"
              v-if="CorrectContactTelephone && ContactTelephone"
            ></i>
            <i
              id="cross-right"
              class="fa-solid fa-circle-xmark"
              v-if="!CorrectContactTelephone && ContactTelephone"
            ></i>
          </div>
        </div>
      </div>
      <div class="row-four">
        <div class="fax-number">
          <label for="fax">Contact Fax</label><br />
          <div class="fax-number-input" >
            <input type="tel" id="fax" name="phone" pattern="[\d\s()+-]*" v-model="FaxNumber" @input="ValidateFaxNumber" placeholder="E.g., +1 (555) 123-4567"/>
            <i
              class="fa-solid fa-circle-check"
              id="tick-left"
              v-if="CorrectFaxNumber && FaxNumber"
            ></i>
            <i
              id="cross-left"
              class="fa-solid fa-circle-xmark"
              v-if="!CorrectFaxNumber && FaxNumber"
            ></i>
          </div>
        </div>
        <div class="contact-email">
          <label for="email">Contact Email</label><br />
          <div class="email-input">
            <input type="email" id="email" name="email" v-model="email" @input="ValidateEmail" placeholder="example@example.com"/>
            <i
              class="fa-solid fa-circle-check"
              id="tick-right"
              v-if="CorrectEmail && email"
            ></i>
            <i
              id="cross-right"
              class="fa-solid fa-circle-xmark"
              v-if="!CorrectEmail && email"
            ></i>
          </div>
        </div>
      </div>
    </div>
    <div class="bottom-layer">
    <div class="steps">
      <span id="current-step">3</span> of <span id="total-steps">12</span>
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
    const country = ref('');
    const city = ref('')
    const ContactPerson = ref('');
    const CorrectContactPerson= ref(false);
    const organization = ref('');
    const CorrectOrganization = ref(false);
    const MailAddress = ref('');
    const CorrectMailAddress = ref(false);
    const ContactTelephone = ref('');
    const CorrectContactTelephone = ref(false);
    const FaxNumber = ref('');
    const CorrectFaxNumber = ref(false);
    const email = ref('');
    const CorrectEmail = ref(false);
    const v$ = useValidate();

    const handleRightClick = () =>{
      // const { emit } = getCurrentInstance(); // Access emit function using getCurrentInstance
      // Emit an event to the parent component to validate and proceed
      // Ensure that the necessary data is filled
      
        // Emit an event to the parent component
        // This event is caught in the parent component to proceed to the next step
        console.log('emiting');
        const data = {
        country: country.value,
        city: city.value,
        ContactPerson: ContactPerson.value,
        ContactTelephone: ContactTelephone.value,
        CorrectContactPerson: CorrectContactPerson.value,
        CorrectContactTelephone: CorrectContactTelephone.value,
        organization: organization.value,
        CorrectOrganization: CorrectOrganization.value,
        MailAddress: MailAddress.value,
        CorrectMailAddress: CorrectMailAddress.value,
        FaxNumber: FaxNumber.value,
        CorrectFaxNumber: CorrectFaxNumber.value,
        
      };
      // Emit the 'update-data' event with the updated data
      emit("update-data", data);
        emit('validate-and-proceed-form-three');
        console.log(city.value)
      
    };

    const handleLeftClick = () => {
      emit('MoveBackToTwo');
    }

    const ValidateContactPerson= ()=>{
      CorrectContactPerson.value = ContactPerson.value.length >= 4 && ContactPerson.value.length < 101;
    } 

    const ValidateOrganization= ()=>{
      CorrectOrganization.value = organization.value.length >= 2 && organization.value.length < 101;
    } 

    const ValidateMailAddress= ()=>{
      CorrectMailAddress.value = MailAddress.value.length >= 3 && MailAddress.value.length < 101;
    } 

    const ValidateContactTelephone= ()=>{
      const ContactTelephonePattern = /^[\d\s()+-]*$/;
      CorrectContactTelephone.value = ContactTelephone.value.length >= 3 && ContactTelephone.value.length < 16 && ContactTelephonePattern.test(ContactTelephone.value);
    } 

    const ValidateFaxNumber = () => {
      const faxNumberPattern = /^[\d\s()+-]*$/;
      CorrectFaxNumber.value = faxNumberPattern.test(FaxNumber.value) && FaxNumber.value.length>=3 && FaxNumber.value.length<=15;
    };

    const ValidateEmail= () =>{
      const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      CorrectEmail.value = emailPattern.test(email.value);
    }


    



    return {
      v$,
      CorrectContactPerson,
      ContactPerson,
      CorrectOrganization,
      organization,
      CorrectMailAddress,
      MailAddress,
      ContactTelephone,
      CorrectContactTelephone,
      CorrectEmail,
      email,
      FaxNumber,
      handleLeftClick,
      CorrectFaxNumber,
      ValidateContactPerson,
      ValidateOrganization,
      ValidateMailAddress,
      ValidateFaxNumber,
      ValidateContactTelephone,
      ValidateEmail,
      handleRightClick,
      city,
      country,
    };
  }
  };
</script>

<style scoped>
.body {
  padding: 0;
  margin: 0;
}

.bottom {
  display: flex;
  /* align-items: center; */
  justify-content: space-evenly;
  gap: 82px;
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
  justify-content: center;
  align-items: center;
  gap: 18px;
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
  padding: 11px 32px 32px 17px;
  max-width: 100%;
}

.row-one,
.row-two,
.row-three,
.row-four {
  display: flex;
  justify-content: space-evenly;
  gap: 35px;
}

.heading {
  position: relative;
  right: 150px;
}

label {
  position: relative;
  left: -40px;
  bottom: 3px;
}

#cross-left{
 position: absolute;
 right: 356px;
 margin-top: 12px;
 color: crimson;
}

#cross-right{
  position: absolute;
  right: 59px;
  margin-top: 12px;
  color: crimson;

}

#tick-left{
 position: absolute;
 right: 356px;
 margin-top: 12px;
 color: green;
}

#tick-right{
  position: absolute;
  right: 59px;
   margin-top: 12px;
  color: green;
}


.country label {
  left: -70px;
}

.organization label,
.city label {
  left: -56px;
}

.contact-telephone label {
  left: -32px;
}

.fax-number label,
.contact-email label {
  left: -55px;
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
  width: 257px;
  height: 41px;
  font-style: italic;
  box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.2);
  text-indent: 22px;
  font-weight: 300;
  box-sizing: border-box;
  margin-left: 4px;
}

select {
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
  width: 257px;
  height: 41px;
  font-style: italic;
  box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.2);
  text-indent: 22px;
  font-weight: 300;
  box-sizing: border-box;
  margin-left: 4px;
}
</style>
