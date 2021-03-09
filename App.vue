<template>
  <Appheader />
  <div class="progress grid grid-cols-3 px-11 mt-3">
    <div
      class="progress-step"
      :class="{'active': currentstep >= 1}"
    >
      <p class="text-center">1</p>
      <p class="mr-2 mt-1">Personal</p>
    </div>
    <div
      class="progress-step"
      :class="{'active': currentstep >= 2}"
    >
      <p class="text-center">2</p>
      <p class="mt-1">ADDRESS</p>
    </div>
    <div
      class="progress-step"
      :class="{'active': currentstep >= 3}"
    >
      <p class="text-center">3</p>
      <p class="mt-1">EMPLOYER</p>
    </div>
  </div>

  <div v-if="currentstep === 1" class="px-11">    
    <form class="grid grid-cols-4 mt-4 pl-8">
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
      <div class="mt-3">
        <label class="mr-1 block">Gender</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.gender'>
          <option>Male</option>
          <option>Female</option>
        </select>
      </div>
      <div class="mt-3">
        <label class="mr-1 block">Marital Staus</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.maritalstatus'>
          <option selected>Select</option>
          <option>Single</option>
          <option>Married</option>
          <option>Divorced</option>
          <option>Widowed</option>
        </select>
      </div>
      <div class="mt-3">
        <label class="mr-1 block">Maiden Name</label>
        <input class="form-input rounded border-black border w-56 h-8" type="text" v-model="registration.maidenname" placeholder="Maiden Name">
      </div>
      <div class="mt-3">
        <label class="mr-1 block">Place of Birth</label>
        <input class="rounded border-black border h-8 w-56" type="text" v-model="registration.placeofbirth">
      </div>
      <div class="mt-3">
        <label class="mr-1 block">Date of Birth</label>
        <input class="form-input rounded border-black border h-8 w-56" type="date" v-model="registration.dob">
      </div>
      <div class="mt-3">
        <label class="mr-1 block">Nationality</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.nationality'>
          <option selected>Select</option>
          <option>Nigeria</option>
          <option>Austria</option>
          <option>Australia</option>
        </select>
      </div>
      <div class="mt-3">
        <label class="mr-1 block">State of Origin</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.stateoforigin'>
          <option>Abia</option>
          <option>Adamawa</option>
          <option>Akwa-Ibom</option>
        </select>
      </div>
      <div class="mt-3">
        <label class="mr-1 block">LGA of Origin</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.lgaoforigin'>
          <option>Amuwo Odofin</option>
          <option>Ikorodu</option>
          <option>Kosofe</option>
        </select>
      </div>
      <div class="mt-3">
        <label class="mr-1 block">Other PFA</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.otherpfa'>
          <option selected value="1">Choose PFA</option>
          <option>Stanbic Pension</option>
          <option>ARM</option>
          <option>PAL</option>
        </select>
      </div>
      <div class="mt-3">
        <label class="mr-1 block">Other Pin</label>
        <input class="rounded border-black border h-8 w-56" type="text" v-model="registration.bvn">
      </div>
      <div class="mt-3">
        <label class="mr-1 block">PIN</label>
        <input class="rounded border-black border h-8 w-56" disabled type="text" v-model="registration.pin">
      </div>
      <div class="mt-3">
        <label class="mr-1 block">Physically Challenged</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.challenged'>
          <option>No</option>
          <option>Yes</option>
        </select>
      </div>
      <div class="mt-3">
        <label class="mr-1 block">Means of Identification</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.moi'>
          <option>NIMC</option>
          <option>Voter's Card</option>
          <option>Driver's License</option>
          <option>Employee ID card</option>
        </select>
      </div>
      <div class="mt-3">
        <label class="mr-1 block">Valid Card Number</label>
        <input class="rounded border-black border h-8 w-56" type="text" v-model="registration.cardnumber">
      </div>
      <div class="mt-3">
        <label class="mr-1 block">BVN</label>
        <input class="rounded border-black border h-8 w-56" type="text" v-model="registration.bvn">
      </div>
      <div class="mt-3">
        <label class="mr-1 block">NIN</label>
        <input class="rounded border-black border h-8 w-56" type="text" v-model="registration.nin">
      </div>
    </form>
  </div>

  <div v-if="currentstep === 2">
    <form class="ml-5">
      <div>
        <label class="mr-2">House Number/Name</label>
        <input class="rounded border-black border h-8 w-7/12 mt-4 ml-11" type="text" v-model="registration.houseno">
      </div>
      <div>
        <label class="mr-2">Street Name</label>
        <input class="rounded border-black border h-8 w-7/12 mt-4 ml-28" type="text" v-model="registration.houseno">
      </div>
      <div>
        <label class="mr-2">Village/Town/City</label>
        <input class="rounded border-black border h-8 w-7/12 mt-4 ml-16" type="text" v-model="registration.villagetown">
      </div>
    </form>
  </div>

  <div class="text-right mr-5">
    <button class="bg-green-600 shadow-md h-11 mr-2 text-white px-2 py-1 rounded font-bold mt-6" @click.prevent="next()">Save and Continue</button>
    <button class="bg-red-600 shadow-md h-11 text-white px-2 py-1 rounded font-bold">Save and Continue Later</button>
  </div>
</template>

<script>
import { ref } from 'vue';
import Appheader from './components/Appheader';
export default {
  components:{ Appheader },
  setup(){
    const currentstep = ref(1)
    const registration = ref([
      {customertitle:'Select title'},
      {surname:'jaijdifjad'}
    ])

    function next() {
      currentstep.value++
    }

    return {currentstep, registration, next}
  }
}
</script>

<style>

.progress-step {
  position: relative;
  width: 30px;
  height: 30px;
  border-radius: 50%;
  margin-bottom: 20px;
  color: #fff;
  background-color: #DF5C2E;
  font-weight: bold;
}

.active {
  background-color: #DF5C2E;
}

.progress-step {
  color: #555;
  background-color: #ccc;
}

.progress-step::before {
  background-color: #ccc;
}

:before {
  content: '';
  position: absolute;
  top: -10px;
  width: 2px;
  height: 20px;
  background: #DF5C2E;
  z-index: 10;
}

:first-child::before {
  display: none;
}
</style>