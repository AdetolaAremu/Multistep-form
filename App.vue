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
        <label>Select Sector</label>
        <select class="rounded border-black border h-8 w-7/12 mt-4 ml-14" v-model="registration.sector">
          <option>Select Sector</option>
          <option>Private</option>
          <option>Federal</option>
          <option>State</option>
        </select>
      </div>
      <div v-if="registration.sector !== 'Private'">
        <div >
          <label class="mr-2">Service ID No(Police/Paramilitary)</label>
          <input class="rounded border-black border h-8 w-7/12 mt-4 ml-28" type="text" v-model="registration.streetname">
        </div>
        <div class="grid grid-cols-2">
          <div>
            <label>Customer Under IPPIS</label>
            <select class="rounded border-black border h-8 w-80 mt-4 ml-14">
              <option selected value="1">Select here</option>
              <option value="2">Yes</option>
              <option value="3">No</option>
            </select>
          </div>
          <div class="mt-2 -ml-10">
            <label class="">IPPIS Number</label>
            <input class="rounded border-black border h-8 w-80 ml-5 mt-2" type="text" placeholder="Enter IPPIS number here" v-model="registration.mobilenumber">
          </div>
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
          <button class="bg-purple-600 rounded px-1 py-1 mt-1 w-24 text-white font-bold" @click.prevent="add">ADD</button>
        </div>
      </div>
      <div class="grid grid-cols-4 mt-2">
        <div>
          <label class="block">Employer Name</label>
          <input type="text" class="h-8 w-56 rounded border border-black" v-model="registration.employername">
        </div>
        <div>
          <label class="block">Employer ID</label>
          <input type="text" class="h-8 w-56 rounded border border-black bg-gray-200" disabled v-model="registration.employerid">
        </div>
        <div>
          <label class="block">Employer Code</label>
          <input type="text" class="h-8 w-56 rounded border border-black bg-gray-200" disabled v-model="registration.employercode">
        </div>
        <div>
          <label class="block">Date of Retirement (If retired)</label>
          <input type="date" class="h-8 w-56 rounded border border-black" v-model="registration.dateofretirement">
        </div>
      </div>
      <div class="grid grid-cols-4 mt-2">
        <div>
          <label class="block">Date of First Employment</label>
          <input type="date" class="h-8 w-56 rounded border border-black" v-model="registration.dateofemployment">
        </div>
        <div>
          <label class="block">Date of Appointment</label>
          <input type="date" class="h-8 w-56 rounded border border-black" v-model="registration.dateofappointment">
        </div>
        <div>
          <label class="block">Date of Transfer of Service</label>
          <input type="date" class="h-8 w-56 rounded border border-black" v-model="registration.servicetransfer">
        </div>
        <div>
          <label class="block">Date of Current Employment</label>
          <input type="date" class="h-8 w-56 rounded border border-black" v-model="registration.currentemployment">
        </div>
      </div>
      <div class="grid grid-cols-4 mt-2">
        <div>
          <label class="block">Monthly Total Emolnument</label>
          <input type="text" class="h-8 w-56 rounded border border-black" v-model="registration.totalemolument">
        </div>
        <div>
          <label class="block">Employer Monthly Contribution</label>
          <input type="text" class="h-8 w-56 rounded border border-black" v-model="registration.employecont">
        </div>
        <div>
          <label class="block">Employee Monthly Contribution</label>
          <input type="text" class="h-8 w-56 rounded border border-black" v-model="registration.employeecont">
        </div>
        <div>
          <label class="block">Voluntary Contribution</label>
          <input type="date" class="h-8 w-56 rounded border border-black" v-model="registration.voluntarycont">
        </div>
      </div>
      <div class="grid grid-cols-4 mt-2">
        <div>
          <label class="block">Employer Industry</label>
          <input type="text" class="h-8 w-56 rounded border border-black" v-model="registration.employerindustry">
        </div>
        <div>
          <label class="block">Qualification</label>
          <select v-model="registration.qualification" class="h-8 w-56 rounded border border-black">
            <option value="1" selected>Bsc</option>
            <option value="2">HND</option>
            <option value="3">PGD</option>
            <option value="4">Msc</option>
            <option value="5">MBA</option>
            <option value="6">Ssce</option>
          </select>
        </div>
        <div>
          <label class="block">Occupation</label>
          <select v-model="registration.occupation" class="h-8 w-56 rounded border border-black">
            <option value="1" selected>Banker</option>
            <option value="2">Admin</option>
          </select>
        </div>
        <div>
          <label class="block font-semibold">Employer Building No/Name</label>
          <input type="date" class="h-8 w-56 rounded border border-black" v-model="registration.employerno">
        </div>
      </div>
      <div class="grid grid-cols-4 mt-2">
        <div>
          <label class="block font-semibold">Employer Streetname</label>
          <input type="text" class="h-8 w-56 rounded border border-black" v-model="registration.employerstreet">
        </div>
        <div>
          <label class="block font-semibold">Employer Country</label>
          <select v-model="registration.employercountry" class="h-8 w-56 rounded border border-black">
            <option value="1" selected>Nigeria</option>
            <option value="2">Australia</option>
          </select>
        </div>
        <div>
          <label class="block font-semibold">Employer State</label>
          <select v-model="registration.employerstate" class="h-8 w-56 rounded border border-black">
            <option value="1" selected>Lagos</option>
            <option value="2">Abia</option>
          </select>
        </div>
        <div>
          <label class="block font-semibold">Employer LGA</label>
          <select v-model="registration.employerlga" class="h-8 w-56 rounded border border-black">
            <option value="1" selected>Somolu</option>
            <option value="2">Ikorodu</option>
          </select>
        </div>
      </div>
      <div class="grid grid-cols-4 mt-2">
        <div>
          <label class="block">Village/Town/City</label>
          <input type="text" class="h-8 w-56 rounded border border-black" v-model="registration.villagetowncity">
        </div>
        <div>
          <label class="block">Postal Code</label>
          <input type="text" class="h-8 w-56 rounded border border-black" v-model="registration.postalcode">
        </div>
        <div>
          <label class="block">Employer Contact Number</label>
          <input type="date" class="h-8 w-56 rounded border border-black" v-model="registration.servicetransfer">
        </div>
        <div>
          <label class="block">Designation</label>
          <input type="date" class="h-8 w-56 rounded border border-black" v-model="registration.currentemployment">
        </div>
      </div>
    </form>
    <div class="text-right mr-5">
      <button class="bg-yellow-600 shadow-md h-11 mr-2 text-white px-2 py-1 rounded font-bold mt-6" @click.prevent="prev()">Previous Page</button>
      <button class="bg-green-600 shadow-md h-11 mr-2 text-white px-2 py-1 rounded font-bold mt-6" @click.prevent="next()">Save and Continue</button>
      <button class="bg-red-600 shadow-md h-11 text-white px-2 py-1 rounded font-bold">Save and Continue Later</button>
    </div>
  </div>

  <div v-if="currentstep === 4">
    <form class="mt-7 ml-16 px-11 grid grid-cols-4">
      <div>
        <label class="mr-1 block">Next of Kin Title</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.customertitle'>
          <option selected>Select title</option>
          <option>Mr</option>
          <option>Mrs</option>
          <option>Miss</option>
        </select>
      </div>
      <div>
        <label class="mr-1 block">Next of Kin Surname</label>
        <input class="form-input rounded border-black border w-56 h-8" type="text" v-model="registration.noksurname">
      </div>
      <div>
        <label class="mr-1 block">Next of Kin First Name</label>
        <input class="form-input rounded border-black border w-56 h-8" type="text" v-model="registration.nokfirstname">
      </div>
      <div>
        <label class="mr-1 block">Next of Kin Middle Name</label>
        <input class="form-input rounded border-black border w-56 h-8" type="text" v-model="registration.nokmiddlename">
      </div>
      <div class="mt-3">
        <label class="mr-1 block">Next of kin Gender</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.nokgender'>
          <option>Male</option>
          <option>Female</option>
        </select>
      </div>
      <div>
        <label class="mr-1 block">Next of Kin Relationship</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.nokrelationship'>
          <option selected>Select Relationship</option>
          <option>Spouse</option>
          <option>Husband</option>
          <option>Wife</option>
        </select>
      </div>
      <div>
        <label class="block">Next of Kin Mobile Number</label>
        <input type="text" class="h-8 w-56 rounded border border-black" v-model="registration.noknumber">
      </div>
      <div>
        <label class="block">Next of Kin Alternate Number</label>
        <input type="text" class="h-8 w-56 rounded border border-black" v-model="registration.nokalternatenumber">
      </div>
      <div class="mt-3">
        <label class="block">Email Address</label>
        <input type="email" class="h-8 w-56 rounded border border-black" v-model="registration.nokemail">
      </div>
      <div class="mt-3">
        <label class="mr-1 block">Next of Kin Nationality</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.noknationality'>
          <option selected>Select Country</option>
          <option>Nigeria</option>
          <option>Austria</option>
          <option>Australia</option>
        </select>
      </div>
      <div class="mt-3">
        <label class="mr-1 block">Next of Kin State of Origin</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.nokstateoforigin'>
          <option>Abia</option>
          <option>Adamawa</option>
          <option>Akwa-Ibom</option>
        </select>
      </div>
      <div class="mt-3">
        <label class="mr-1 block">Next of Kin LGA of Origin</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.noklgaoforigin'>
          <option>Amuwo Odofin</option>
          <option>Ikorodu</option>
          <option>Kosofe</option>
        </select>
      </div>
      <div class="mt-3">
        <label class="mr-1 block">Village/Town/City</label>
        <input type="text" class="h-8 rounded border border-black w-56" v-model="registration.nokvillage">
      </div>
      <div class="mt-3">
        <label class="mr-1 block">Postal Code</label>
        <input type="text" class="h-8 rounded border border-black w-56" v-model="registration.nokpostalcode">
      </div>
      <div class="mt-3">
        <label class="mr-1 block">House Number/Name</label>
        <input type="text" class="h-8 rounded border border-black w-56" v-model="registration.nokhouseno">
      </div>
      <div class="mt-3">
        <label class="mr-1 block">Streetname</label>
        <input type="text" class="h-8 rounded border border-black w-56" v-model="registration.nokstreetname">
      </div>
    </form>
    <div class="text-right mr-5">
      <button class="bg-yellow-600 shadow-md h-11 mr-2 text-white px-2 py-1 rounded font-bold mt-6" @click.prevent="prev()">Previous Page</button>
      <button class="bg-green-600 shadow-md h-11 mr-2 text-white px-2 py-1 rounded font-bold mt-6" @click.prevent="next()">Save and Continue</button>
      <button class="bg-red-600 shadow-md h-11 text-white px-2 py-1 rounded font-bold">Save and Continue Later</button>
    </div>
  </div>
  <div v-if="currentstep === 5">
    <form class="mt-7 ml-16 px-11 grid grid-cols-4">
      <div>
        <div class="w-full h-max justify-center bg-grey-lighter">
          <label class="w-64 flex flex-col items-center px-3 py-3 bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 cursor-pointer hover:bg-blue-700 hover:text-white">
            <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
             <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
            </svg>
            <span class="mt-2 text-sm leading-normal font-bold">Upload Passport</span>
            <input type='file' class="hidden" />
          </label>
        </div>
      </div>
      <div>
        <div class="w-full h-max justify-center bg-grey-lighter">
          <label class="w-64 flex flex-col items-center px-3 py-3 bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 cursor-pointer hover:bg-blue-700 hover:text-white">
            <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
             <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
            </svg>
            <span class="mt-2 text-sm leading-normal font-bold">Upload Signature</span>
            <input type='file' class="hidden" />
          </label>
        </div>
      </div>
      <div>
        <div class="w-full h-max justify-center bg-grey-lighter">
          <label class="w-64 flex flex-col items-center px-3 py-3 bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 cursor-pointer hover:bg-blue-700 hover:text-white">
            <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
             <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
            </svg>
            <span class="mt-2 text-sm leading-normal font-bold">Upload Birth Certificate</span>
            <input type='file' class="hidden" />
          </label>
        </div>
      </div>
      <div>
        <div class="w-full h-max justify-center bg-grey-lighter">
          <label class="w-64 flex flex-col items-center px-3 py-3 bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 cursor-pointer hover:bg-blue-700 hover:text-white">
            <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
             <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
            </svg>
            <span class="mt-2 text-sm leading-normal font-bold">Upload Employment Letter</span>
            <input type='file' class="hidden" />
          </label>
        </div>
      </div>
      <div>
        <div class="w-full h-max justify-center bg-grey-lighter">
          <label class="w-64 flex flex-col items-center px-3 py-3 bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 cursor-pointer hover:bg-blue-700 hover:text-white">
            <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
             <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
            </svg>
            <span class="mt-2 text-sm leading-normal font-bold">Means of Identification</span>
            <input type='file' class="hidden" />
          </label>
        </div>
      </div>
      <div>
        <div class="w-full h-max justify-center bg-grey-lighter">
          <label class="w-64 flex flex-col items-center px-3 py-3 bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 cursor-pointer hover:bg-blue-700 hover:text-white">
            <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
             <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
            </svg>
            <span class="mt-2 text-sm leading-normal font-bold">Proof of Address</span>
            <input type='file' class="hidden" />
          </label>
        </div>
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

    const sectors = ref([
      {name:'Private', value:'1'},
      {name:'Federal', value:'2'},
      {name:'Cross-border', value:'3'},
      {name:'Informal', value:'4'},
      {name:'Others', value:'5'}
    ])

    const add = () => {
      registration.value.push({structure:'', grade:'', step:'', salary:''})
    }

    const remove = (index) => {
      registration.value.splice(index, 1)
    }

    const registration = ref([
      {structure:'', grade:'', step:'', salary:'', sector:''}
    ])

    function next() {
      currentstep.value++
    }

    function prev() {
      currentstep.value--
    }

    return {currentstep, registration, next, prev, salarystructure, add, remove, sectors}
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