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
    <div class="text-right mr-5">
      <button class="bg-green-600 shadow-md h-11 mr-2 text-white px-2 py-1 rounded font-bold mt-6" @click.prevent="next()">Save and Continue</button>
      <button class="bg-red-600 shadow-md h-11 text-white px-2 py-1 rounded font-bold">Save and Continue Later</button>
    </div>
  </div>

  <div v-if="currentstep === 2">
    <form class="ml-16 px-11">
      <div>
        <label class="mr-2">House Number/Name</label>
        <input class="rounded border-black border h-8 w-7/12 mt-4 ml-11" type="text" v-model="registration.houseno">
      </div>
      <div>
        <label class="mr-2">Street Name</label>
        <input class="rounded border-black border h-8 w-7/12 mt-4 ml-28" type="text" v-model="registration.streetname">
      </div>
      <div>
        <label class="mr-2">Village/Town/City</label>
        <input class="rounded border-black border h-8 w-7/12 mt-4" style="margin-left: 4.7rem" type="text" v-model="registration.villagetown">
      </div>
      <div>
        <label>Country of Residence</label>
        <select class="rounded border-black border h-8 w-7/12 mt-4 ml-14">
          <option selected value="1">Nigeria</option>
          <option value="2">Niger</option>
        </select>
      </div>
      <div>
        <label>State of Residence</label>
        <select class="rounded border-black border h-8 w-7/12 mt-4" style="margin-left: 4.7rem">
          <option selected value="1">Abia</option>
          <option value="2">Adamawa</option>
        </select>
      </div>
      <div>
        <label>LGA of Residence</label>
        <select class="rounded border-black border h-8 w-7/12 mt-4" style="margin-left: 5.1rem">
          <option selected value="1">Surulere</option>
          <option value="2">Shomolu</option>
        </select>
      </div>
      <div class="mt-3 grid grid-cols-3">
        <div>
          <label class="block mb-1">Mobile Number</label>
          <input class="rounded border-black border h-8 w-7/12" type="number" v-model="registration.mobilenumber">
        </div>
        <div class="-ml-36 mb-1">
          <label class="block">Alternate Number</label>
          <input class="rounded border-black border h-8 w-7/12" type="number" v-model="registration.alternatenumber">
        </div>
        <div class="-ml-52 mb-1">
          <label class="block">Update Email Address</label>
          <input class="rounded border-black border h-8 w-6/12" type="email" v-model="registration.emailaddress">
        </div>
      </div>
    </form>
    <div class="text-right mr-5">
      <button class="bg-yellow-600 shadow-md h-11 mr-2 text-white px-2 py-1 rounded font-bold mt-6" @click.prevent="prev()">Previous Page</button>
      <button class="bg-green-600 shadow-md h-11 mr-2 text-white px-2 py-1 rounded font-bold mt-6" @click.prevent="next()">Save and Continue</button>
      <button class="bg-red-600 shadow-md h-11 text-white px-2 py-1 rounded font-bold">Save and Continue Later</button>
    </div>
  </div>

  <div v-if="currentstep === 3">
    <form class="ml-16 px-11">
      <div>
        <label>Please sector Sector</label>
        <select class="rounded border-black border h-8 w-7/12 mt-4 ml-14">
          <option selected value="1">Private</option>
          <option value="2">Federal</option>
          <option value="3">State</option>
          <option value="4">Cross-border</option>
          <option value="5">Others</option>
        </select>
      </div>
      <div >
        <label class="mr-2">Service ID No(Police/Paramilitary)</label>
        <input class="rounded border-black border h-8 w-7/12 mt-4 ml-28" type="text" v-model="registration.streetname">
      </div>
      <div class="mt-2">
        <label>Date of Current Appointment</label>
        <input class="form-input rounded border-black border h-8 w-56" type="date">
      </div>
      <div>
        <label>Customer Under IPPIS</label>
        <select class="rounded border-black border h-8 w-7/12 mt-4 ml-14">
          <option selected value="1">Select here</option>
          <option value="2">Yes</option>
          <option value="3">No</option>
        </select>
      </div>
      <div class="mt-2">
        <label class="">IPPIS Number</label>
        <input class="rounded border-black border h-8 w-60" type="number" v-model="registration.mobilenumber">
      </div>
      <div class="mt-3">
        <div v-for="(register, index) in registration" :key="index" class="grid grid-cols-5">
          <div>
            <label class="block">Salary structure</label>
            <select class="rounded border-black border h-8 w-60" v-model="register.structure">
              <option selected value="1">Select here</option>
              <option v-for="entry in salarystructure" :key="entry">{{ entry.date }}</option>
           </select>
          </div>
          <div>
            <label class="block">Grade Level</label>
            <input type="text" class="border border-black rounded w-52 h-8" v-model="register.grade">
          </div>
          <div>
            <label class="block">Grade Step</label>
            <input type="text" class="border border-black rounded w-52 h-8" v-model="register.step">
          </div>
          <div>
            <label class="block">Salary</label>
            <input type="text" class="border border-black rounded w-52 h-8" v-model="register.salary">
          </div>
          <div>
            <button class="bg-red-600 mt-6 rounded px-1 py-1 w-24 text-white font-bold" @click.prevent="remove(index)">X</button>   
          </div>
        </div>
        <button class="bg-purple-600 rounded px-1 py-1 text-white font-bold" @click.prevent="add">ADD</button>
      </div>
    </form>
  </div>

  
</template>

<script>
import { ref } from 'vue';
import Appheader from './components/Appheader';
export default {
  components:{ Appheader },
  setup(){
    const currentstep = ref(1)
    const salarystructure = ref([
      {date: '2019'},
      {date: '2016'},
      {date: '2013'},
      {date: '2010'},
      {date: '2007'},
      {date: '2004'}
    ]);

    const add = () => {
      registration.value.push({structure:'', grade:'', step:'', salary:''})
    }

    const remove = (index) => {
      registration.value.splice(index, 1)
    }

    const registration = ref([
      {structure:'', grade:'', step:'01', salary:''}
    ])

    function next() {
      currentstep.value++
    }

    function prev() {
      currentstep.value--
    }

    return {currentstep, registration, next, prev, salarystructure, add, remove}
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
  color: #DF5C2E;
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