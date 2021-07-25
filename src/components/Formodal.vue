<template>
  <div @click="closemodal">
    <div v-if="showmodal">
      <section class="bg-gray-200 h-full w-full fixed top-0 left-0 z-10 opacity-50"></section>
      <div class="inset-0 absolute h-full flex">
        <div class="m-auto z-20 bg-white rounded h-60 w-80">
          <p>
            <slot name="body"></slot>
          </p>
          <p>
            <slot name="footer"></slot>
          </p>
        </div>
      </div>
    </div>
  </div>

  <!-- <section
    @click="close"
    class="z-20 h-screen w-screen bg-gray-500 fixed top-0 left-0 opacity-50"
  ></section>
  <div class="absolute inset-0">
    <div class="flex h-full">
      <div class="z-30 m-auto bg-white p-2 rounded shadow w-10/12 md:w-1/3">
        <div class="p-2 border">
          <h1 class="text-2xl">
            <slot name="title"></slot>
          </h1>
          <main>
            <slot name="body"></slot>
          </main>
        </div>
      </div>
    </div>
  </div> -->
</template>

<script>
export default {
  data(){
    return {
      showmodal:true
    }
  },
  methods: {
    closemodal() {
      emit('closemodal')
    }
  }

  //   setup(_, { emit }) {
  //   function close() {
  //     emit("close");
  //   }
  //   return { close };
  // },

}
</script>

<style>
