<template>  
  <div v-if="modalopen">
    <section
      class="z-20 h-screen w-screen bg-gray-500 fixed top-0 left-0 opacity-50"
    ></section>
    <div class="absolute inset-0">
      <div class="flex h-full">
        <div class="z-30 m-auto bg-white p-2 rounded-md shadow w-10/12 md:w-1/3">
          <div class="p-2 border">
            <p class="text-center font-bold">THIS IS A MULTI-STEP FORM</p>
            <p>
              There are six(6) steps in the form, starting from:
            </p>
            <p><span class="font-semibold">Step 1:</span> Personal details of the client</p>
            <p><span class="font-semibold">Step 2:</span> Contact details of the client</p>
            <p><span class="font-semibold">Step 3:</span> Employment details of the client</p>
            <p><span class="font-semibold">Step 4:</span> Next of Kin details of the client</p>
            <p><span class="font-semibold">Step 5:</span> Upload relevant documents</p>
            <p><span class="font-semibold">Step 6:</span> Review data</p>
            <div class="text-center">
              <button class="bg-red-600 text-white font-semibold p-2 rounded-md mt-2" 
                @click="modalopen = false"
              >
                Close Modal
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // setup(_, { emit }) {
  //   function close() {
  //     emit("close");
  //   }
  //   return { close };
  // },

  data(){
    return{
      modalopen:true
    }
  }

}
</script>

<style>
</style>