<template>
  <div v-if="currentstep === 1" class="px-11">
    <form class="grid grid-cols-4">
      <div>
        <label class="block">Title</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.customertitle'>
          <option selected>Select title</option>
          <option>Mr</option>
          <option>Mrs</option>
          <option>Miss</option>
        </select>
      </div>
      <div>
        <label class="mr-1 block">Surname</label>
        <input class="form-input rounded border-black border w-56 h-8" type="text" v-model="registration.surname">
      </div>
      <div>
        <label class="mr-1 block">First Name</label>
        <input class="form-input rounded border-black border w-56 h-8" type="text" v-model="registration.firstname">
      </div>
      <div>
        <label class="mr-1 block">Middle Name</label>
        <input class="form-input rounded border-black border w-56 h-8" type="text" v-model="registration.middlename">
      </div>
      <div>
        <label class="mr-1 block">Gender</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.gender'>
          <option>Male</option>
          <option>Female</option>
        </select>
      </div>
      <div>
        <label class="mr-1 block">Marital Staus</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.maritalstatus'>
          <option selected>Select</option>
          <option>Single</option>
          <option>Married</option>
          <option>Divorced</option>
          <option>Widowed</option>
        </select>
      </div>
      <div>
        <label class="mr-1 block">Maiden Name</label>
        <input class="form-input rounded border-black border w-56 h-8" type="text" v-model="registration.maidenname" placeholder="Maiden Name">
      </div>
      <div>
        <label class="mr-1 block">Place of Birth</label>
        <input class="rounded border-black border h-8 w-56" type="text" v-model="registration.placeofbirth">
      </div>
      <div>
        <label class="mr-1 block">Date of Birth</label>
        <input class="form-input rounded border-black border h-8 w-56" type="text" v-model="registration.dob">
      </div>
      <div>
        <label class="mr-1 block">Nationality</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.nationality'>
          <option selected>Select</option>
          <option>Nigeria</option>
          <option>Austria</option>
          <option>Australia</option>
        </select>
      </div>
      <div>
        <label class="mr-1 block">State of Origin</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.stateoforigin'>
          <option>Abia</option>
          <option>Adamawa</option>
          <option>Akwa-Ibom</option>
        </select>
      </div>
      <div>
        <label class="mr-1 block">LGA of Origin</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.lgaoforigin'>
          <option>Amuwo Odofin</option>
          <option>Ikorodu</option>
          <option>Kosofe</option>
        </select>
      </div>
      <div>
        <label class="mr-1 block">Other PFA</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.otherpfa'>
          <option>Stanbic Pension</option>
          <option>ARM</option>
          <option>PAL</option>
        </select>
      </div>
      <div>
        <label class="mr-1 block">Other Pin</label>
        <input class="rounded border-black border h-8 w-56" type="text" v-model="registration.bvn">
      </div>
      <div>
        <label class="mr-1 block">PIN</label>
        <input class="rounded border-black border h-8 w-56" disabled type="text" v-model="registration.pin">
      </div>
      <div>
        <label class="mr-1 block">Physically Challenged</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.challenged'>
          <option>No</option>
          <option>Yes</option>
        </select>
      </div>
      <div>
        <label class="mr-1 block">Means of Identification</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.moi'>
          <option>NIMC</option>
          <option>Voter's Card</option>
          <option>Driver's License</option>
          <option>Employee ID card</option>
        </select>
      </div>
      <div>
        <label class="mr-1 block">Valid Card Number</label>
        <input class="rounded border-black border h-8 w-56" disabled type="text" v-model="registration.cardnumber">
      </div>
      <div>
        <label class="mr-1 block">BVN</label>
        <input class="rounded border-black border h-8 w-56" type="text" v-model="registration.bvn">
      </div>
      <div>
        <label class="mr-1 block">NIN</label>
        <input class="rounded border-black border h-8 w-56" type="text" v-model="registration.nin">
      </div>
    </form>
  </div>

  <div>
    <button class="bg-green-600 shadow-md text-white px-1 py-1 rounded font-bold">Save and Continue</button>
    <button class="bg-red-600 shadow-md text-white px-1 py-1 rounded font-bold">Save and Continue Later</button>
  </div>
</template>

<script>
import { ref } from 'vue'
export default {
  setup(){
    const currentstep = ref(1)
    const registration = ref([
      {customertitle:'Select title'},
      {surname:''}
    ])

    return {currentstep, registration}
  }
}
</script>

<style>

</style>