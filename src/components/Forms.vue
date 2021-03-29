<template>  
  <Formodal />
  <div class='container'>
    <ul class="progressbar">
      <li class="hidden" :class="{'active': currentstep === 1}"><p>Step 1</p></li>
      <li :class="{'active': currentstep >= 2}"><p>Step 2</p></li>
      <li :class="{'active': currentstep >= 3}"><p>Step 3</p></li>
      <li :class="{'active': currentstep >= 4}"><p>Step 4</p></li>
      <li :class="{'active': currentstep >= 5}"><p>Step 5</p></li>
      <li :class="{'active': currentstep >= 6}"><p>Step 6</p></li>
    </ul>
  </div>

  <div v-show="currentstep === 1" class="px-20 py-5 mt-28 bg-white h-full">    
    <form @submit="checkform">
      <div class="grid grid-cols-1 pl-8 -ml-14 sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4">
        <!-- <Formodal>
          <template v-slot:body>
            jdifjidjfidjsijiji
          </template>
        </Formodal>         -->
        <p v-if="errors.length">
          <b>Please correct these errors:</b>
          <ul>
            <li v-for="error in errors" :key="error">{{ error }}</li>
          </ul>
        </p>
        <div>
          <label class="block">Title</label>
          <select class="rounded border-black border w-56 h-8 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" v-model='registration.title'>
            <option disabled value=''>Select title</option>
            <option>Mr</option>
            <option>Mrs</option>
            <option>Miss</option>
          </select>
        </div>
        <div>
          <label class="mr-1 block">Surname</label>
          <input class="form-input rounded border-black border w-56 h-8 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" type="text" v-model="registration.surname">
        </div>
        <div>
          <label class="mr-1 block">First Name</label>
          <input  class="form-input rounded border-black border w-56 h-8 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" type="text" v-model="registration.firstname" @blur="v$.registration.firstname.$touch">
          <div v-if="v$.registration.firstname.$error" class="text-red-600">Mandatory field</div>
        </div>
        <div>
          <label class="mr-1 block">Middle Name</label>
          <input class="form-input rounded border-black border w-56 h-8 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" type="text" v-model="registration.middlename">
        </div>
        <div class="mt-3">
          <label class="mr-1 block">Gender</label>
          <select class="rounded border-black border w-56 h-8 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" v-model='registration.gender'>
            <option disabled value="">Choose Gender</option>
            <option>Male</option>
            <option>Female</option>
          </select>
        </div>
        <div class="mt-3">
          <label class="mr-1 block">Marital Staus</label>
          <select class="rounded border-black border w-56 h-8 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" v-model='registration.maritalstatus'>
            <option disabled value="">Select Marital Status</option>
            <option>Single</option>
            <option>Married</option>
            <option>Divorced</option>
            <option>Widowed</option>
          </select>
        </div>
        <div class="mt-3">
          <label class="mr-1 block">Maiden Name</label>
          <input class="form-input rounded border-black border w-56 h-8 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" type="text" v-model="registration.maidenname">
        </div>
        <div class="mt-3">
          <label class="mr-1 block">Place of Birth</label>
          <input class="rounded border-black border h-8 w-56 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" type="text" v-model="registration.placeofbirth">
        </div>
        <div class="mt-3">
          <label class="mr-1 block">Date of Birth</label>
          <input class="form-input rounded border-black border h-8 w-56 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" type="date" v-model="registration.dob">
        </div>
        <div class="mt-3">
          <label class="mr-1 block">Nationality</label>
          <select class="rounded border-black border w-56 h-8 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" v-model='registration.nationality'>
            <option selected value="">Select Nationaality</option>
            <option>Nigeria</option>
            <option>Austria</option>
            <option>Australia</option>
          </select>
        </div>
        <div class="mt-3">
          <label class="mr-1 block">State of Origin</label>
          <select class="rounded border-black border w-56 h-8 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" v-model='registration.stateoforigin'>
            <option selected value="">Select State of Origin</option>
            <option>Abia</option>
            <option>Adamawa</option>
            <option>Akwa-Ibom</option>
          </select>
        </div>
        <div class="mt-3">
          <label class="mr-1 block">LGA of Origin</label>
          <select class="rounded border-black border w-56 h-8 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" v-model='registration.lgaoforigin'>
            <option selected value="">Select LGA of Origin</option>
            <option>Amuwo Odofin</option>
            <option>Ikorodu</option>
            <option>Kosofe</option>
          </select>
        </div>
        <div class="mt-3">
          <label class="mr-1 block">Other PFA</label>
          <select class="rounded border-black border w-56 h-8 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" v-model='registration.otherpfa'>
            <option selected value="">Choose PFA</option>
            <option>Stanbic Pension</option>
            <option>ARM</option>
            <option>PAL</option>
          </select>
        </div>
        <div class="mt-3">
          <label class="mr-1 block">Other Pin</label>
          <input class="rounded border-black border h-8 w-56 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" type="text" v-model="registration.otherpin">
        </div>
        <div class="mt-3">
          <label class="mr-1 block">PIN</label>
          <input class="rounded border-black border h-8 w-56 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" disabled type="text" v-model="registration.pin">
        </div>
        <div class="mt-3">
          <label class="mr-1 block">Physically Challenged</label>
          <select class="rounded border-black border w-56 h-8 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" v-model='registration.challenged'>
            <option selected value="">Select</option>
            <option>No</option>
            <option>Yes</option>
          </select>
        </div>
        <div class="mt-3">
          <label class="mr-1 block">Means of Identification</label>
          <select class="rounded border-black border w-56 h-8 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" v-model='registration.moi'>
            <option selected value="">Select MOI</option>
            <option>NIMC</option>
            <option>Voter's Card</option>
            <option>Driver's License</option>
            <option>Employee ID card</option>
          </select>
        </div>
        <div class="mt-3">
          <label class="mr-1 block">Valid Card Number</label>
          <input class="rounded border-black border h-8 w-56 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" type="text" v-model="registration.cardnumber">
        </div>
        <div class="mt-3">
          <label class="mr-1 block">BVN</label>
          <input class="rounded border-black border h-8 w-56 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" type="text" v-model="registration.bvn">
        </div>
        <div class="mt-3">
          <label class="mr-1 block">NIN</label>
          <input class="rounded border-black border h-8 w-56 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" type="text" v-model="registration.nin">
        </div>
      </div>
    <div class="text-right">
      <button class="bg-green-600 shadow-md h-11 mr-2 text-white px-2 py-1 rounded font-bold mt-6" @click.prevent="next()">Save and Continue</button>
      <button class="bg-yellow-600 shadow-md h-11 mr-2 text-white px-2 py-1 rounded font-bold mt-6" @click.prevent="prev()">Previous Page</button>
    </div>
    </form>
  </div>

  <div v-show="currentstep === 2" class="bg-white h-full mt-28 py-5">
    <form class="ml-5">
      <div>
        <div class="flex flex-row">
          <label class="">House Number/Name <span class="font-bold text-lg text-red-600"> *</span></label>
          <input class="rounded border-black border h-8 w-7/12 ml-11 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" type="text" v-model="registration.houseno">
        </div>
        <div class="flex flex-row mt-3">
          <label class="">Street Name <span class="font-bold text-lg text-red-600"> *</span></label>
          <input class="rounded border-black border h-8 w-7/12 ml-28 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" type="text" v-model="registration.streetname">
        </div>
        <div class="flex flex-row mt-3">
          <label class="text-md sm:text-sm md:text-md">Village /Town / City <span class="font-bold text-lg text-red-600"> *</span></label>
          <input class="rounded border-black border h-8 w-7/12 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" style="margin-left: 4.7rem" type="text" v-model="registration.villagetown">
        </div>
        <div class="flex flex-row mt-3">
          <label>Country of Residence <span class="font-bold text-lg text-red-600"> *</span></label>
          <select class="rounded border-black border h-8 w-7/12 ml-12 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" v-model="registration.countryofresidence">
            <option selected value="">Nigeria</option>
            <option>Niger</option>
          </select>
        </div>
        <div class="flex flex-row mt-3">
          <label>State of Residence <span class="font-bold text-lg text-red-600"> *</span></label>
          <select class="rounded border-black border h-8 w-7/12 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" style="margin-left: 4.35rem" v-model="registration.stateofresidence">
            <option selected value="">Abia</option>
            <option value="2">Adamawa</option>
          </select>
        </div>
        <div class="flex flex-row mt-3">
          <label>LGA of Residence <span class="font-bold text-lg text-red-600"> *</span></label>
          <select class="rounded border-black border h-8 w-7/12 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" style="margin-left: 4.8rem" v-model="registration.lgaofresidence">
            <option selected value="">Surulere</option>
            <option value="2">Shomolu</option>
          </select>
        </div>
      </div>
      <div class="grid grid-cols-1 mt-3 sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4">
        <div>
          <label class="block">Mobile Number <span class="font-bold text-lg text-red-600"> *</span></label>
          <input class="rounded border-black border h-8 w-11/12 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" type="text" v-model="registration.mobilenumber">
        </div>
        <div class="">
          <label class="block">Alternate Number</label>
          <input class="rounded border-black border h-8 w-11/12 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" type="text" v-model="registration.alternatenumber">
        </div>
        <div class="">
          <label class="block">Update Email Address</label>
          <input class="rounded border-black border h-8 w-11/12 focus:outline-none focus:ring-1 focus:ring-indigo-500 focus:border-indigo-500" type="email" v-model="registration.emailaddress">
        </div>
      </div>
    </form>
    <div class="text-right mr-5">
      <button class="bg-yellow-600 shadow-md h-11 mr-2 text-white px-2 py-1 rounded font-bold mt-6" @click.prevent="prev()">Previous Page</button>
      <button class="bg-green-600 shadow-md h-11 mr-2 text-white px-2 py-1 rounded font-bold mt-6" @click.prevent="next()">Save and Continue</button>
      <button class="bg-red-600 shadow-md h-11 text-white px-2 py-1 rounded font-bold">Save and Continue Later</button>
    </div>
  </div>

  <div v-if="currentstep === 3" class="bg-white h-full py-5 mt-28">
    <form class="ml-5 sm:px-0 md:px-0 lg:px-16">
      <div class="selectsector">
        <label class="block sm:block md:block lg:inline-block">Select Sector</label>
        <select class="rounded border-black border h-8 w-9/12 sm:w-9/12 md:w-9/12 lg:w-7/12 ml-3" v-model="registration.sector">
          <option disabled value="">Select Sector</option>
          <option>Private</option>
          <option>Federal</option>
          <option>State</option>
        </select>
      </div>
      <div v-show="registration.sector !== 'Private'">
        <div class="mt-3">
          <label class="block sm:block md:block lg:inline-block">Service ID No</label>
          <input class="rounded border-black border h-8 w-9/12 sm:w-9/12 md:w-9/12 lg:w-7/12 ml-2" type="text" v-model="registration.serviceid">
        </div>
        <div class="flex flex-col gap-3 lg:flex-row md:flex-row">
          <div class="mt-2">
            <label class="block sm:block md:block lg:block">Under IPPIS ?</label>
            <select class="rounded border-black border h-8 w-64 mt-1" v-model="registration.underippis">
              <option disabled value="">Select here</option>
              <option>Yes</option>
              <option>No</option>
            </select>
          </div>
          <div class="mt-2">
            <label class="block sm:block md:block lg:block">IPPIS Number</label>
            <input class="rounded border-black border h-8 w-64 mt-1" type="text" placeholder="Enter IPPIS number here" v-model="registration.ippisnumber">
          </div>
        </div>
        <div class="mt-3">
          <div v-for="(register, index) in reel" :key="index" class="grid sm:grid-cols-1 md:grid-cols-1 lg:grid-cols-5">
            <div class="gap-2">
              <label class="block">Salary structure</label>
              <select class="rounded border-black border h-8 w-60" v-model="register.structure">
                <option disabled value="">Select here</option>
                <option v-for="entry in salarystructure" :key="entry">{{ entry.date }}</option>
              </select>
            </div>
            <div class="">
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
      <div class="grid mt-4 sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-4">
        <div>
          <label class="block">Employer Name<span class="font-bold text-lg text-red-600"> *</span></label>
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
      <div class="grid mt-4 sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-4">
        <div>
          <label class="block">Date of First Employment<span class="font-bold text-lg text-red-600"> *</span></label>
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
      <div class="grid mt-4 sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-4">
        <div>
          <label class="block">Monthly Total Emolnument</label>
          <input type="text" class="h-8 w-56 rounded border border-black" v-model="registration.totalemolument">
        </div>
        <div>
          <label class="block">Employer Monthly Contribution</label>
          <input type="text" class="h-8 w-56 rounded border border-black" v-model="registration.employercont">
        </div>
        <div>
          <label class="block">Employee Monthly Contribution</label>
          <input type="text" class="h-8 w-56 rounded border border-black" v-model="registration.employeecont">
        </div>
        <div>
          <label class="block">Voluntary Contribution</label>
          <input type="type" class="h-8 w-56 rounded border border-black" v-model="registration.voluntarycont">
        </div>
      </div>
      <div class="grid mt-4 sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-4">
        <div>
          <label class="block">Employer Industry</label>
          <input type="text" class="h-8 w-56 rounded border border-black" v-model="registration.employerindustry">
        </div>
        <div>
          <label class="block">Qualification</label>
          <select class="h-8 w-56 rounded border border-black" v-model="registration.qualification">
            <option disabled value="">Select Qualification</option>
            <option>Bsc</option>
            <option>HND</option>
            <option>PGD</option>
            <option>Msc</option>
            <option>MBA</option>
            <option>Ssce</option>
          </select>
        </div>
        <div>
          <label class="block">Occupation</label>
          <select class="h-8 w-56 rounded border border-black" v-model="registration.occupation">
            <option disabled value="">Select Occupation</option>
            <option>Banker</option>
            <option>Admin</option>
          </select>
        </div>
        <div>
          <label class="block">Employer Building No/Name <span class="font-bold text-lg text-red-600"> *</span></label>
          <input type="type" class="h-8 w-56 rounded border border-black" v-model="registration.employerbuildingno">
        </div>
      </div>
      <div class="grid mt-4 sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-4">
        <div>
          <label class="block">Employer Streetname <span class="font-bold text-lg text-red-600"> *</span></label>
          <input type="text" class="h-8 w-56 rounded border border-black" v-model="registration.employerstreet">
        </div>
        <div>
          <label class="block">Employer Country<span class="font-bold text-lg text-red-600"> *</span></label>
          <select class="h-8 w-56 rounded border border-black" v-model="registration.employercountry">
            <option value="">Nigeria</option>
            <option>Australia</option>
          </select>
        </div>
        <div>
          <label class="block">Employer State <span class="font-bold text-lg text-red-600"> *</span></label>
          <select class="h-8 w-56 rounded border border-black" v-model="registration.employerstate">
            <option value="">Lagos</option>
            <option value="2">Abia</option>
          </select>
        </div>
        <div>
          <label class="block">Employer LGA<span class="font-bold text-lg text-red-600"> *</span></label>
          <select class="h-8 w-56 rounded border border-black" v-model="registration.employerlga">
            <option value="">Somolu</option>
            <option value="2">Ikorodu</option>
          </select>
        </div>
      </div>
      <div class="grid mt-4 sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-4">
        <div>
          <label class="block">Village/Town/City<span class="font-bold text-lg text-red-600"> *</span></label>
          <input type="text" class="h-8 w-56 rounded border border-black" v-model="registration.villagetowncity">
        </div>
        <div>
          <label class="block">Postal Code</label>
          <input type="text" class="h-8 w-56 rounded border border-black" v-model="registration.postalcode">
        </div>
        <div>
          <label class="block">Employer Contact Number<span class="font-bold text-lg text-red-600"> *</span></label>
          <input type="text" class="h-8 w-56 rounded border border-black" v-model="registration.employercontactno">
        </div>
        <div>
          <label class="block">Designation</label>
          <input type="text" class="h-8 w-56 rounded border border-black" v-model="registration.designation">
        </div>
      </div>
    </form>
    <div class="text-right mr-5">
      <button class="bg-yellow-600 shadow-md h-11 mr-2 text-white px-2 py-1 rounded font-bold mt-6" @click.prevent="prev()">Previous Page</button>
      <button class="bg-green-600 shadow-md h-11 mr-2 text-white px-2 py-1 rounded font-bold mt-6" @click.prevent="next()">Save and Continue</button>
      <button class="bg-red-600 shadow-md h-11 text-white px-2 py-1 rounded font-bold">Save and Continue Later</button>
    </div>
  </div>

  <div v-show="currentstep === 4" class="bg-white h-full mt-28 py-5">
    <form class="grid ml-16 mt-7 sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-4">
      <div>
        <label class="mr-1 block">Next of Kin Title</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.noktitle'>
          <option disabled value="">Select title</option>
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
          <option disabled value="">Select Gender</option>
          <option>Male</option>
          <option>Female</option>
        </select>
      </div>
      <div>
        <label class="mr-1 block">Next of Kin Relationship</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.nokrelationship'>
          <option disabled value="">Select Relationship</option>
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
          <option value="">Nigeria</option>
          <option>Austria</option>
          <option>Australia</option>
        </select>
      </div>
      <div class="mt-3">
        <label class="mr-1 block">Next of Kin State of Residence</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.nokstateofresidence'>
          <option value="">Abia</option>
          <option>Adamawa</option>
          <option>Akwa-Ibom</option>
        </select>
      </div>
      <div class="mt-3">
        <label class="mr-1 block">Next of Kin LGA of Residence</label>
        <select class="rounded border-black border w-56 h-8" v-model='registration.noklgaofresidence'>
          <option disabled value="">Amuwo Odofin</option>
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

  <div class="py-5 mt-28 bg-white h-full" v-show="currentstep === 5">
    <div>
      <p class="font-bold text-center sm:text-sm md:text-sm lg:text-lg">
        Upload your passport, signature and other supporting 
        document in <span class="text-red-600 font-bold">JPEG, JPG and PNG</span> as stated in each upload box, <span class="text-red-600 font-bold">file size should not exceed 500kb</span>
      </p>
    </div>
    <form class="mt-5 px-11 ml-2">
      <div class="grid sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-4">
        <div>
          <div class="w-64 h-36 justify-center bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 hover:bg-blue-700 hover:text-white overflow-x-hidden">
            <label class="w-64 flex flex-col items-center px-3 py-2 cursor-pointer">
              <span class="mt-2 text-sm leading-normal font-bold">Upload Passport<span class="font-bold text-lg text-red-600"> *</span></span>
              <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
              <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
              </svg>
            </label>
            <input class="ml-2 py-2" type='file' @change="onFileChangepassport" />
          </div>
        </div>
        <div>
          <div class="w-64 h-36 justify-center bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 hover:bg-blue-700 hover:text-white overflow-x-hidden">
            <label class="w-64 flex flex-col items-center px-3 py-2 cursor-pointer">
              <span class="mt-2 text-sm leading-normal font-bold">Upload Signature<span class="font-bold text-lg text-red-600"> *</span></span>
              <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
              <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
              </svg>
            </label>
            <input class="ml-2 py-2" type='file' @change="onFileChangesignature" />
          </div>
        </div>
        <div>
          <div class="w-64 h-36 justify-center bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 hover:bg-blue-700 hover:text-white overflow-x-hidden">
            <label class="w-64 flex flex-col items-center px-3 py-2 cursor-pointer">
              <span class="mt-2 text-sm leading-normal font-bold">Birth Certificate<span class="font-bold text-lg text-red-600"> *</span></span>
              <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
              <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
              </svg>
            </label>
            <input class="ml-2 py-2" type='file'>
          </div>
        </div>
        <div>
          <div class="w-64 h-36 justify-center bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 hover:bg-blue-700 hover:text-white overflow-x-hidden">
            <label class="w-64 flex flex-col items-center px-3 py-2 cursor-pointer">
              <span class="mt-2 text-sm leading-normal font-bold">Employment Letter<span class="font-bold text-lg text-red-600"> *</span></span>
              <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
              <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
              </svg>
            </label>
            <input class="ml-2 py-2" type='file'>
          </div>
        </div>
        <div class="mt-1">
          <div class="w-64 h-36 justify-center bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 hover:bg-blue-700 hover:text-white overflow-x-hidden">
            <label class="w-64 flex flex-col items-center px-3 py-2">
              <span class="mt-2 text-sm leading-normal font-bold">Means of Identification<span class="font-bold text-lg text-red-600"> *</span></span>
              <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
              <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
              </svg>
            </label>
            <input class="ml-2 py-2" type='file'>
          </div>
        </div>
        <div class="mt-1">
          <div class="w-64 h-36 justify-center bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 hover:bg-blue-700 hover:text-white overflow-x-hidden">
            <label class="w-64 flex flex-col items-center px-3 py-2 cursor-pointer">
              <span class="mt-2 text-sm leading-normal font-bold">Proof of Address<span class="font-bold text-lg text-red-600"> *</span></span>
              <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
              <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
              </svg>
            </label>
            <input class="ml-2 py-2" type='file'>
          </div>
        </div>
      </div>
      <div v-if="registration.sector !== 'Private'" class="mt-5">
        <div><p class="font-bold text-center mb-2 sm:text-sm md:text-sm lg:text-lg">Public Sector participant, upload salary structure as stated in the upload boxes below</p></div>
        <div class="grid sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-4">
          <div>
            <div class="w-64 h-36 justify-center bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 hover:bg-blue-700 hover:text-white overflow-x-hidden">
              <label class="w-64 flex flex-col items-center px-3 py-2">
                <span class="mt-2 text-sm leading-normal font-bold">Harmonized Salary 2004<span class="font-bold text-lg text-red-600"> *</span></span>
                <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
                </svg>
              </label>
              <input class="ml-2 py-2" type='file'>
            </div>
          </div>
          <div>
            <div class="w-64 h-36 justify-center bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 hover:bg-blue-700 hover:text-white overflow-x-hidden">
              <label class="w-64 flex flex-col items-center px-3 py-2">
                <span class="mt-2 text-sm leading-normal font-bold">Consolidated Salary 2007<span class="font-bold text-lg text-red-600"> *</span></span>
                <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
                </svg>
              </label>
              <input class="ml-2 py-2" type='file'>
            </div>
          </div>
          <div>
            <div class="w-64 h-36 justify-center bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 hover:bg-blue-700 hover:text-white overflow-x-hidden">
              <label class="w-64 flex flex-col items-center px-3 py-2">
                <span class="mt-2 text-sm leading-normal font-bold">Consolidated Salary 2010<span class="font-bold text-lg text-red-600"> *</span></span>
                <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
                </svg>
              </label>
              <input class="ml-2 py-2" type='file'>
            </div>
          </div>
          <div>
            <div class="w-64 h-36 justify-center bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 hover:bg-blue-700 hover:text-white overflow-x-hidden">
              <label class="w-64 flex flex-col items-center px-3 py-2">
                <span class="mt-2 text-sm leading-normal font-bold">Harmonized Salary 2013<span class="font-bold text-lg text-red-600"> *</span></span>
                <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
                </svg>
              </label>
              <input class="ml-2 py-2" type='file'>
            </div>
          </div>
          <div class="mt-1">
            <div class="w-64 h-36 justify-center bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 hover:bg-blue-700 hover:text-white overflow-x-hidden">
              <label class="w-64 flex flex-col items-center px-3 py-2">
                <span class="mt-2 text-sm leading-normal font-bold">Harmonized Salary 2016<span class="font-bold text-lg text-red-600"> *</span></span>
                <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
                </svg>
              </label>
              <input class="ml-2 py-2" type='file'>
            </div>
          </div>
          <div class="mt-1">
            <div class="w-64 h-36 justify-center bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 hover:bg-blue-700 hover:text-white overflow-x-hidden">
              <label class="w-64 flex flex-col items-center px-3 py-2">
                <span class="mt-2 text-sm leading-normal font-bold">Current Salary<span class="font-bold text-lg text-red-600"> *</span></span>
                <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
                </svg>
              </label>
              <input class="ml-2 py-2" type='file'>
            </div>
          </div>
        </div>
      </div>
      <div class="mt-5">
        <div><p class="font-bold text-center mb-2 sm:text-sm md:text-sm lg:text-lg">Kindly upload additional/supporting documents here (Optional)</p></div>
        <div class="grid sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-4">
          <div>
            <div class="w-64 h-36 justify-center bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 hover:bg-blue-700 hover:text-white overflow-x-hidden">
              <label class="w-64 flex flex-col items-center px-3 py-2">
                <span class="mt-2 text-sm leading-normal font-bold">Additional Document 1</span>
                <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
                </svg>
              </label>
              <input class="ml-2 py-2" type='file'>
            </div>
          </div>
          <div>
            <div class="w-64 h-36 justify-center bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 hover:bg-blue-700 hover:text-white overflow-x-hidden">
              <label class="w-64 flex flex-col items-center px-3 py-2">
                <span class="mt-2 text-sm leading-normal font-bold">Additional Document 2</span>
                <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
                </svg>
              </label>
              <input class="ml-2 py-2" type='file'>
            </div>
          </div>
          <div>
            <div class="w-64 h-36 justify-center bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 hover:bg-blue-700 hover:text-white overflow-x-hidden">
              <label class="w-64 flex flex-col items-center px-3 py-2">
                <span class="mt-2 text-sm leading-normal font-bold">Additional Document 3</span>
                <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
                </svg>
              </label>
              <input class="ml-2 py-2" type='file'>
            </div>
          </div>
          <div>
            <div class="w-64 h-36 justify-center bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 hover:bg-blue-700 hover:text-white overflow-x-hidden">
              <label class="w-64 flex flex-col items-center px-3 py-2">
                <span class="mt-2 text-sm leading-normal font-bold">Additional Document 4</span>
                <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
                </svg>
              </label>
              <input class="ml-2 py-2" type='file'>
            </div>
          </div>
          <div class="mt-1">
            <div class="w-64 h-36 justify-center bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 hover:bg-blue-700 hover:text-white overflow-x-hidden">
              <label class="w-64 flex flex-col items-center px-3 py-2">
                <span class="mt-2 text-sm leading-normal font-bold">Additional Document 5</span>
                <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
                </svg>
              </label>
              <input class="ml-2 py-2" type='file'>
            </div>
          </div>
          <div class="mt-1">
            <div class="w-64 h-36 justify-center bg-white text-blue rounded-lg shadow-lg tracking-wide uppercase border border-blue-500 hover:bg-blue-700 hover:text-white overflow-x-hidden">
              <label class="w-64 flex flex-col items-center px-3 py-2">
                <span class="mt-2 text-sm leading-normal font-bold">Additional Document 6</span>
                <svg class="w-8 h-8 mt-3" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                <path d="M16.88 9.1A4 4 0 0 1 16 17H5a5 5 0 0 1-1-9.9V7a3 3 0 0 1 4.52-2.59A4.98 4.98 0 0 1 17 8c0 .38-.04.74-.12 1.1zM11 11h3l-4-4-4 4h3v3h2v-3z" />
                </svg>
              </label>
              <input class="ml-2 py-2" type='file'>
            </div>
          </div>
        </div>
      </div>
    </form>
    <div class="text-right mr-5">
      <button class="bg-yellow-600 shadow-md h-11 mr-2 text-white px-2 py-1 rounded font-bold mt-6" @click.prevent="prev()">Previous Page</button>
      <button class="bg-green-600 shadow-md h-11 mr-2 text-white px-2 py-1 rounded font-bold mt-6" @click.prevent="next()">Save and Continue</button>
      <button class="bg-red-600 shadow-md h-11 text-white px-2 py-1 rounded font-bold">Save and Continue Later</button>
    </div>
  </div>
  
  <div v-show="currentstep === 6" class="px-10 py-5 bg-white h-full mt-28">
    <div class="mt-4">
      <div>
        <div><p class="text-lg font-bold text-center bg-gray-500 text-white mt-3 mb-2">BIOMETRICS</p></div>
        <div class=" flex flex-col justify-center gap-3 lg:flex-row md:flex-row">
          <div class="border border-black h-52 w-64 bg-white my-4 shadow-md text-center">
            <img :src="passport" class="h-44 w-64" />
            <div class="text-center font-semibold pt-2">PASSPORT</div>
          </div>
          <div class="border border-black h-52 w-64 bg-white my-4 shadow-md">
            <img :src="signature" class="h-44 w-64" />
            <div class="text-center font-semibold pt-2">SIGNATURE</div>
          </div>
        </div>
      </div>
      <div><p class="text-lg font-bold text-center bg-gray-500 text-white mt-6 mb-2">PERSONAL INFORMATION</p></div>
      <div class="grid sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-3">
        <div>
          <div><p><span class="font-bold">Title:</span> {{ registration.title }}</p></div>
        </div>
        <div>
          <div><p><span class="font-bold">Surname:</span> {{ registration.surname }}</p></div>
        </div>
        <div>
          <div><p><span class="font-bold">First name:</span> {{ registration.firstname }}</p></div>
        </div>
        <div class="mt-2">
          <div><p><span class="font-bold">Middle name:</span> {{ registration.middlename }}</p></div>
        </div>
        <div class="mt-2">
          <div><p><span class="font-bold">Gender:</span> {{ registration.gender }}</p></div>
        </div>
        <div class="mt-2">
          <div><p><span class="font-bold">Marital Status:</span> {{ registration.maritalstatus }}</p></div>
        </div>
        <div class="mt-2">
          <div><p><span class="font-bold">Maiden Name:</span> {{ registration.maidenname }}</p></div>
        </div>
        <div class="mt-2">
          <div><p><span class="font-bold">Place Of Birth:</span> {{ registration.placeofbirth }}</p></div>
        </div>
        <div class="mt-2">
          <div><p><span class="font-bold">dob:</span> {{ registration.dob }}</p></div>
        </div>
        <div class="mt-2">
          <div><p><span class="font-bold">Nationality:</span> {{ registration.nationality }}</p></div>
        </div>
        <div class="mt-2">
          <div><p><span class="font-bold">State Of Origin:</span> {{ registration.stateoforigin }}</p></div>
        </div>
        <div class="mt-2">
          <div><p><span class="font-bold">LGA of Origin:</span> {{ registration.lgaoforigin }}</p></div>
        </div>
        <div class="mt-2">
          <div><p><span class="font-bold">Other PFA:</span> {{ registration.otherpfa }}</p></div>
        </div>
        <div class="mt-2">
          <div><p><span class="font-bold">Physically Challenged:</span> {{ registration.challenged }}</p></div>
        </div>
        <div class="mt-2">
          <div><p><span class="font-bold">Means of Identification:</span> {{ registration.moi }}</p></div>
        </div>
        <div class="mt-2">
          <div><p><span class="font-bold">Card Number:</span> {{ registration.cardnumber }}</p></div>
        </div>
        <div class="mt-2">
          <div><p><span class="font-bold">BVN:</span> {{ registration.bvn }}</p></div>
        </div>
        <div class="mt-2">
          <div><p><span class="font-bold">NIN:</span> {{ registration.nin }}</p></div>
        </div>
      </div>
      <div>
        <div><p class="text-lg font-bold text-center bg-gray-500 text-white mt-3 mb-2">CONTACT DETAILS</p></div>
        <div class="grid sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-2">
          <div>
            <div><p><span class="font-bold">House Number:</span> {{ registration.houseno }}</p></div>
          </div>
          <div>
            <div><p><span class="font-bold">Street Name:</span> {{ registration.streetname }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Village/Town/City:</span> {{ registration.villagetown }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Country of Residence:</span> {{ registration.countryofresidence }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">State of Residence:</span> {{ registration.stateofresidence }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">LGA of Residence:</span> {{ registration.lgaofresidence }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Mobile Number:</span> {{ registration.mobilenumber }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Alternate Number:</span> {{ registration.alternatenumber }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Email Address:</span> {{ registration.email }}</p></div>
          </div>
        </div>
      </div>
      <div>
        <div><p class="text-lg font-bold text-center bg-gray-500 text-white mt-3 mb-2">EMPLOYMENT DETAILS</p></div>
        <div class="grid sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-2">
          <div>
            <div><p><span class="font-bold">Sector</span> {{ registration.sector }}</p></div>
          </div>
          <div>
            <div><p><span class="font-bold">Service ID:</span> {{ registration.serviceid }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Under IPPIS:</span> {{ registration.underippis }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">IPPIS Number:</span> {{ registration.ippisnumber }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Employer Name:</span> {{ registration.employername }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Date of First Employment:</span> {{ registration.dateofemployment }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Date of Retirement:</span> {{ registration.dateofretirement }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Date of Appointment:</span> {{ registration.dateofappointment }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Current Employment:</span> {{ registration.currentemployment }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Service Transfer:</span> {{ registration.servicetransfer }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Total Emolnument:</span> {{ registration.totalemolument }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Employer Contribution:</span> {{ registration.employercont }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Employee Contribution:</span> {{ registration.employeecont }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Voluntary Contribution:</span> {{ registration.voluntarycont }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Employer Industry:</span> {{ registration.employerindustry }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Qualification:</span> {{ registration.qualification }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Occupation:</span> {{ registration.occupation }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Employer Building No:</span> {{ registration.employerbuildingno }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Employer Street:</span> {{ registration.employerstreet }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Employer Country:</span> {{ registration.employercountry }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Employer State:</span> {{ registration.employerstate }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Employer LGA:</span> {{ registration.employerlga }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Village/Town/City:</span> {{ registration.villagetowncity }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Postal Code:</span> {{ registration.postalcode }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Employer Contact No:</span> {{ registration.employercontactno }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Designation:</span> {{ registration.designation }}</p></div>
          </div>
        </div>
      </div>
      <div>
        <div>
        <div><p class="text-lg font-bold text-center bg-gray-500 text-white mt-3 mb-2">NEXT OF KIN DETAILS</p></div>
        <div class="grid sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-2">
          <div>
            <div><p><span class="font-bold">Next of Kin Title:</span> {{ registration.noktitle }}</p></div>
          </div>
          <div>
            <div><p><span class="font-bold">Next of Kin Surname:</span> {{ registration.noksurname }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Next of Kin First Name:</span> {{ registration.nokfirstname }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Next of Kin Middlename:</span> {{ registration.nokmiddlename }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Next of Kin Gender:</span> {{ registration.nokgender }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Next of Kin Relationship:</span> {{ registration.nokrelationship }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Next of Kin Mobile Number:</span> {{ registration.noknumber }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Next of Kin Alternate Number:</span> {{ registration.nokalternatenumber }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Next of Kin Email:</span> {{ registration.nokemail }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Next of Kin Nationality:</span> {{ registration.nationality }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Next of Kin State of Residence:</span> {{ registration.nokstateofresidence }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Next of Kin LGA of Residence:</span> {{ registration.noklgaofresidence }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Next of Kin Village:</span> {{ registration.nokvillage }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Next of Kin Postal Code:</span> {{ registration.nokpostalcode }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Next of Kin House No:</span> {{ registration.nokhouseno }}</p></div>
          </div>
          <div class="mt-2">
            <div><p><span class="font-bold">Next of Kin Street Name:</span> {{ registration.nokstreetname }}</p></div>
          </div>
        </div>
      </div>
      <div>
        <div>
        <div><p class="text-lg font-bold text-center bg-gray-500 text-white mt-3 mb-2">ACKNOWLEDGEMENT</p></div>
        <div class="mt-3">
          <label class="block font-bold">Acknowledgement/Cerification</label>
          <textarea cols="30" rows="3" disabled class="border border-black w-full rounded bg-gray-100">
            I (insert name) hereby certify that the information provided or as confirmed by me in this form is true and correct.
            I further consent and authorize Nigeria Inter-Bank Settlement System Plc and National Identity Management Commission to release my BVN
            and or NIN information (as may be required) to the National Pension Commission(Pencom) for the maintenance and operation of my
          </textarea>
          <div>
            <input type="checkbox" class="checked:bg-blue-600 checked:border-transparent rounded h-4 w-4">
            <label class="ml-3 font-bold">I Agree</label>
          </div>
        </div>
      </div>
      </div>
      </div>
    <div class="text-right mr-5 mt-5">
      <button class="bg-yellow-600 shadow-md h-11 mr-2 text-white px-2 py-1 rounded font-bold" @click.prevent="prev()">Previous Page</button>
      <button class="bg-green-600 shadow-md h-11 mr-2 text-white px-2 py-1 rounded font-bold w-40">Submit</button>
    </div>
    </div>
  </div>
</template>

<script>
// import { ref } from 'vue';

import useVuelidate from '@vuelidate/core'
import { required, email } from '@vuelidate/validators';
import Formodal from './Formodal.vue';
export default {
  components: { Formodal },
  setup: () => ({ v$: useVuelidate() }),
  data(){
    return {
      currentstep:1,
      passport:'',
      signature:'',
      errors: [],
      files:'',
      salarystructure: [
        {date: '2019'},
        {date: '2016'},
        {date: '2013'},
        {date: '2010'},
        {date: '2007'},
        {date: '2004'}
      ],

      sectors: [
        {name:'Private', value:'1'},
        {name:'Federal', value:'2'},
        {name:'Cross-border', value:'3'},
        {name:'Informal', value:'4'},
        {name:'Others', value:'5'}
      ],

      reel:[
        {structure:'', grade:'', step:'', salary:''}
      ],

      registration: {  
        title:'', surname:'', firstname:'', middlename:'', gender:'', maritalstatus:'', maidenname:'', placeofbirth:'', dob:'', nationality:'',
        stateoforigin:'', lgaoforigin:'', otherpfa:'', otherpin:'', pin:'', challenged:'', moi:'', cardnumber:'', bvn:'', nin:'',
        houseno:'', streetname:'', villagetown:'', countryofresidence:'', stateofresidence:'', lgaofresidence:'', mobilenumber:'',
        alternatenumber:'', emailaddress:'', sector:'', serviceid:'', underippis:'', structure:'', grade:'', step:'', salary:'',
        employername:'', employerid:'', employercode:'', dateofretirement:'', dateofemployment:'', dateofappointment:'', servicetransfer:'',
        currentemployment:'', totalemolument:'', employercont:'', employeecont:'', voluntarycont:'', employerindustry:'', qualification:'',
        occupation:'', employerbuildingno:'', employerstreet:'', employercountry:'', employerstate:'', employerlga:'', villagetowncity:'',
        postalcode:'', employercontactno:'', designation:'', noktitle:'', noksurname:'', nokfirstname:'', nokmiddlename:'', nokgender:'',
        nokrelationship:'', noknumber:'', nokalternatenumber:'', nokemail:'', noknationality:'', nokstateofresidence:'', noklgaofresidence:'',
        nokvillage:'', nokpostalcode:'', nokhouseno:'', nokstreetname:''
      },
    }
  },
  validations:{
   registration: {
     firstname: {required, $autodirty: true},
     emailaddress: {required, email}
   }
  },
  methods: {
    next() {
      this.currentstep++
    },
    prev(){
      this.currentstep--
    },
    onFileChangepassport(event) {    	   
      const data = URL.createObjectURL(event.target.files[0]);
      this.passport = data;
    },
    onFileChangesignature(event) {    	   
      const data = URL.createObjectURL(event.target.files[0]);
      this.signature = data;
    },
    add(){
      this.reel.push({structure:'', grade:'', step:'', salary:''})
    },
    remove(index){
      this.reel.splice(index, 1)
    },
    submitForm () {
      this.v$.$touch()
      if (!this.v$.$error){
        console.log(`Name: ${this.registration.firstname}`);
      }
    },
    checkform: function(e) {
      if(this.registration.firstname && this.registration.surname){
        return true;
      }
      this.errors = [];

      if(!this.registration.firstname){
        this.errors.push('First name required');
      }
      if (!this.registration.surname) {
        this.errors.push('Surname required')
      }
      e.preventDefault();
    }
  },
}
//   setup(){
//     const currentstep = ref(1)
//     const file = ref([])
//     const url = ref('')
//     const salarystructure = ref([
//       {date: '2019'},
//       {date: '2016'},
//       {date: '2013'},
//       {date: '2010'},
//       {date: '2007'},
//       {date: '2004'}
//     ]);

//     const sectors = ref([
//       {name:'Private', value:'1'},
//       {name:'Federal', value:'2'},
//       {name:'Cross-border', value:'3'},
//       {name:'Informal', value:'4'},
//       {name:'Others', value:'5'}
//     ])

//     const add = () => {
//       registration.value.push({structure:'', grade:'', step:'', salary:''})
//     }
       

//     const remove = (index) => {
//       registration.value.splice(index, 1)
//     }

//     const registration = ref([
//       {
//         title:'', firstname:'', middlename:'', gender:'', maritalstatus:'', maidenname:'', placeofbirth:'', dob:'', nationality:'',
//         stateoforigin:'', lgaoforigin:'', otherpfa:'', otherpin:'', pin:'', challenged:'', moi:'', cardnumber:'', bvn:'', nin:'',
//         houseno:'', streetname:'', villagetown:'', countryofresidence:'', stateofresidence:'', lgaofresidence:'', mobilenumber:'',
//         alternatenumber:'', emailaddress:'', sector:'', serviceid:'', underippis:'', structure:'', grade:'', step:'', salary:'',
//         employername:'', employerid:'', employercode:'', dateofretirement:'', dateofemployment:'', dateofappointment:'', servicetransfer:'',
//         currentemployment:'', totalemolument:'', employercont:'', employeecont:'', voluntarycont:'', employerindustry:'', qualification:'',
//         occupation:'', employerbuildingno:'', employerstreet:'', employercountry:'', employerstate:'', employerlga:'', villagetowncity:'',
//         postalcode:'', employercontactno:'', designation:'', noktitle:'', noksurname:'', nokfirstname:'', nokmiddlename:'', nokgender:'',
//         nokrelationship:'', noknumber:'', nokalternatenumber:'', nokemail:'', noknationality:'', nokstateofresidence:'', noklgaofresidence:'',
//         nokvillage:'', nokpostalcode:'', nokhouseno:'', nokstreetname:''
//       }
//     ])

//     function next() {
//       currentstep.value++
//     }

//     function prev() {
//       currentstep.value--
//     }

//     const fileselected = (e) => {
//       file.value = e.target.file.value[0].name
//     }

//     function onfilechange(e) {
//       const file = e.target.files[0];
//       url.value = URL.createObjectURL(file);
//     }

//     return {currentstep, registration, next, prev, salarystructure, add, remove, sectors, fileselected, file, onfilechange}
//   }
// }
</script>

<style>

.container{
  width: 100%;
  position: absolute;
  z-index: 1;
}

.progressbar li{
  float: left;
  width: 15%;
  position: relative;
  text-align: center;
}

.progressbar li:before{
  content:"";
  width: 30px;
  height: 30px;
}

.progressbar li:before{
  content:"";
  width: 20px;
  height: 30px;
  border: 2px solid #bebebe;
  display: block;
  margin: 0 auto 10px auto;
  border-radius: 50%;
  line-height: 27px;
  background: white;
  color: #bebebe;
  text-align: center;
  font-weight: bold;
}

.progressbar{
  counter-reset: currentstep;
}

.progressbar li:before{
  content:counter(currentstep);
  counter-increment: currentstep;
  width: 30px;
  height: 30px;
  border: 2px solid #bebebe;
  display: block;
  margin: 0 auto 10px auto;
  border-radius: 50%;
  line-height: 27px;
  background: white;
  color: #bebebe;
  text-align: center;
  font-weight: bold;
}

.progressbar li:after{
  content: '';
  position: absolute;
  width: 100%;
  height: 3px;
  background: #979797;
  top: 15px;
  left: -50%;
  z-index: -1;
}

.progressbar li:first-child::after{
  display: none;
}

.progressbar li.active + li::after{
  background: #3aac5d;
}

.progressbar li.active + li::before{
  border-color: #3aac5d;
  background: #3aac5d;
  color: white;
}

body {
  --tw-bg-opacity: 1;
  background-color: rgba(217, 119, 6, var(--tw-bg-opacity));
}
</style>