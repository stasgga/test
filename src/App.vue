<template>
  <div class="w-full flex px-2 py-2 h-screen">
    <div class="w-1/2 h-full py-10 flex justify-center">
      <div class="flex flex-col gap-10">
        <div
          class="flex flex-col w-full"
          v-for="item in specifications"
          v-bind:key="item.id"
        >
          <div
            class="py-1 bg-gray-200 text-center cursor-pointer px-4"
            @click="changeAccordion(item.id)"
          >
            {{ item.name }}
          </div>
          <div
            class="text-center cursor-pointer"
            :class="{ hidden: accordion !== item.id }"
            @click="update(item)"
          >
            <p>Engine - {{ item.engine }}</p>
            <p>Interior materials - {{ item.interiorMaterials }}</p>
            <p>Wheel rims - {{ item.wheelRims }} inches</p>
            <p>Colors - {{ item.color }}</p>
            <p>Air suspensions - {{ item.airSuspension ? 'Yes' : 'No' }}</p>
            <p>Signature on hood - {{ item.signatureOnHood }}</p>
          </div>
        </div>
      </div>
    </div>
    <div class="w-1/2 flex items-center justify-center">
      <div class="flex flex-col gap-2">
        <div class="flex flex-col gap-2">
          <label for="">Name of specification</label>
          <input
            type="text"
            v-model="editing.name"
            class="form-input appearance-none block w-full px-3 py-1.5 text-base font-normal text-gray-700 bg-white bg-clip-padding bg-no-repeat border border-solid border-gray-300 rounded transition ease-in-out m-0 focus:text-gray-700 focus:bg-white focus:border-blue-600 focus:outline-none"
          />
        </div>
        <div class="flex justify-center">
          <div class="mb-3 xl:w-96">
            <div class="flex flex-col gap-2">
              <label for="">Engine</label>
              <select
                v-model="editing.engine"
                class="form-select appearance-none block w-full px-3 py-1.5 text-base font-normal text-gray-700 bg-white bg-clip-padding bg-no-repeat border border-solid border-gray-300 rounded transition ease-in-out m-0 focus:text-gray-700 focus:bg-white focus:border-blue-600 focus:outline-none"
                aria-label="Default select example"
              >
                <option selected>Engine</option>
                <option value="Ferrari Colombo V12">Ferrari Colombo V12</option>
                <option value="BMW S70/2">BMW S70/2</option>
                <option value="Jaguar V12">Jaguar V12</option>
                <option value="Lamborghini V12 L539"
                  >Lamborghini V12 L539</option
                >
                <option value="Ferrari F140">Ferrari F140</option>
                <option value="Mercedes-Benz M120 / M297"
                  >Mercedes-Benz M120 / M297</option
                >
                <option value="Aston Martin NA V12">Aston Martin NA V12</option>
                <option value="Toyota 1GZ-FE">Toyota 1GZ-FE</option>
                <option value="GMA Cosworth V12">GMA Cosworth V12</option>
              </select>
            </div>
          </div>
        </div>
        <div class="flex justify-center">
          <div class="mb-3 xl:w-96">
            <div class="flex flex-col gap-2">
              <label for="">Interior materials</label>
              <select
                v-model="editing.interiorMaterials"
                class="form-select appearance-none block w-full px-3 py-1.5 text-base font-normal text-gray-700 bg-white bg-clip-padding bg-no-repeat border border-solid border-gray-300 rounded transition ease-in-out m-0 focus:text-gray-700 focus:bg-white focus:border-blue-600 focus:outline-none"
                aria-label="Default select example"
              >
                <option value="Leather">Leather</option>
                <option value="Vinyl">Vinyl</option>
                <option value="Wood">Wood</option>
                <option value="Suede">Suede</option>
                <option value="Velour">Velour</option>
                <option value="Faux leather">Faux leather</option>
              </select>
            </div>
          </div>
        </div>
        <div class="flex justify-center">
          <div class="mb-3 xl:w-96">
            <div class="flex flex-col gap-2">
              <label for="">Color</label>
              <select
                v-model="editing.color"
                class="form-select appearance-none block w-full px-3 py-1.5 text-base font-normal text-gray-700 bg-white bg-clip-padding bg-no-repeat border border-solid border-gray-300 rounded transition ease-in-out m-0 focus:text-gray-700 focus:bg-white focus:border-blue-600 focus:outline-none"
                aria-label="Default select example"
              >
                <option value="White">White</option>
                <option value="Black">Black</option>
                <option value="Red">Red</option>
                <option value="Blue">Blue</option>
                <option value="Gray">Gray</option>
                <option value="Yellow">Yellow</option>
              </select>
            </div>
          </div>
        </div>
        <div class="flex justify-center">
          <div class="mb-3 xl:w-96">
            <div class="flex flex-col gap-2">
              <label for="">Wheel rims</label>
              <select
                v-model="editing.wheelRims"
                class="form-select appearance-none block w-full px-3 py-1.5 text-base font-normal text-gray-700 bg-white bg-clip-padding bg-no-repeat border border-solid border-gray-300 rounded transition ease-in-out m-0 focus:text-gray-700 focus:bg-white focus:border-blue-600 focus:outline-none"
                aria-label="Default select example"
              >
                <option value="10">10</option>
                <option value="25">25</option>
                <option value="50">50</option>
                <option value="100">100</option>
              </select>
            </div>
          </div>
        </div>
        <div class="flex justify-center">
          <div class="mb-3 xl:w-96">
            <div class="flex flex-col gap-2">
              <label for="">Type of rims</label>
              <select
                v-model="editing.wheelType"
                class="form-select appearance-none block w-full px-3 py-1.5 text-base font-normal text-gray-700 bg-white bg-clip-padding bg-no-repeat border border-solid border-gray-300 rounded transition ease-in-out m-0 focus:text-gray-700 focus:bg-white focus:border-blue-600 focus:outline-none"
                aria-label="Default select example"
              >
                <option value="Alloy wheels">Alloy wheels</option>
                <option value="Steel wheels">Steel wheels</option>
                <option value="Split wheels">Split wheels</option>
                <option value="Forged and Cast Wheels"
                  >Forged and Cast Wheels</option
                >
              </select>
            </div>
          </div>
        </div>
        <div class="flex justify-center">
          <div>
            <div class="form-check">
              <input
                type="checkbox"
                value=""
                v-model="editing.airSuspension"
                id="flexCheckChecked"
                checked
              />
              <label
                class="form-check-label inline-block text-gray-800"
                for="flexCheckChecked"
              >
                Air suspension
              </label>
            </div>
          </div>
        </div>
        <div class="flex flex-col gap-2">
          <label for="">Signature on hood</label>
          <input
            type="text"
            v-model="editing.signatureOnHood"
            class="form-input appearance-none block w-full px-3 py-1.5 text-base font-normal text-gray-700 bg-white bg-clip-padding bg-no-repeat border border-solid border-gray-300 rounded transition ease-in-out m-0 focus:text-gray-700 focus:bg-white focus:border-blue-600 focus:outline-none"
          />
        </div>
        <div class="flex justify-end">
          <!-- <button class="px-3 py-2 bg-gray-200">
            + new configuration option
          </button> -->
          <button class="px-3 py-2 bg-gray-200" @click="submit">submit</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        specifications: [],
        accordion: 0,
        editing: {
          name: '',
          engine: '',
          interiorMaterials: '',
          color: '',
          wheelType: '',
          airSuspension: false,
          signatureOnHood: '',
        },
      }
    },
    methods: {
      submit() {
        if (this.editing.id) {
          let id = this.specifications.findIndex(
            (e) => e.id === this.editing.id
          )
          this.specifications[id] = this.editing
        } else {
          this.specifications = [
            ...this.specifications,
            { ...this.editing, id: this.specifications.length + 1 },
          ]
        }
        this.editing = {
          name: '',
          engine: '',
          interiorMaterials: '',
          color: '',
          wheelType: '',
          airSuspension: false,
          signatureOnHood: '',
        }
      },
      update(data) {
        this.editing = data
      },
      changeAccordion(id) {
        this.accordion = this.accordion === id ? 0 : id
      },
    },
  }
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
  }
</style>
