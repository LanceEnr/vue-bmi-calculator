<template>
  <section
    class="bg-gray-50 dark:bg-gray-900"
    style="
      background-image: url('https://images.pexels.com/photos/209841/pexels-photo-209841.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1');
      background-size: cover;
    "
  >
    <div
      class="flex flex-col items-center justify-center px-6 py-8 mx-auto md:h-screen lg:py-0"
    >
      <a
        href="#"
        class="flex items-center mb-6 text-2xl font-semibold text-gray-100"
      >
        <img
          class="w-10 h-10 mr-3"
          src="https://upload.wikimedia.org/wikipedia/en/thumb/2/24/Seal_of_the_University_of_Santo_Tomas.svg/1200px-Seal_of_the_University_of_Santo_Tomas.svg.png"
          alt="logo"
        />
        BMI Calculator
      </a>
      <div
        class="w-full bg-white rounded-lg shadow dark:border md:mt-0 sm:max-w-md xl:p-0 dark:bg-gray-800 dark:border-gray-700"
      >
        <div class="p-6 space-y-4 md:space-y-6 sm:p-8">
          <h1
            class="text-xl font-bold leading-tight tracking-tight text-gray-900 md:text-2xl dark:text-white"
          >
            Calculate your BMI here
          </h1>
          <form class="space-y-4 md:space-y-6" action="#">
            <div>
              <label
                for="number"
                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
                >Weight (kg)</label
              >
              <input
                v-model.number="weight"
                type="number"
                min="1"
                class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                placeholder="Weight"
                required=""
              />
            </div>
            <div>
              <label
                for="number"
                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
                >Height (cm)</label
              >
              <input
                v-model.number="height"
                type="number"
                min="1"
                class="bg-gray-50 border border-gray-300 text-gray-900 sm:text-sm rounded-lg focus:ring-primary-600 focus:border-primary-600 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                required=""
                placeholder="Height"
              />
            </div>

            <button
              type="submit"
              @click="calculateBMI"
              class="w-full text-white bg-yellow-600 hover:bg-primary-700 focus:ring-4 focus:outline-none focus:ring-primary-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-primary-600 dark:hover:bg-primary-700 dark:focus:ring-primary-800"
            >
              Calculate BMI
            </button>
          </form>
        </div>
      </div>
      <div
        class="w-full bg-white rounded-lg shadow dark:border md:mt-6 sm:max-w-md xl:p-0 dark:bg-gray-800 dark:border-gray-700"
      >
        <div class="p-6 space-y-4 md:space-y-6 sm:p-8">
          <div class="flex items-center justify-between">
            <h1
              class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
            >
              BMI:
              <p class="text-xl text-yellow-600">{{ bmi }}</p>
            </h1>
            <h1
              class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
            >
              You are:
              <p class="text-xl text-yellow-600">{{ weightStatus }}</p>
            </h1>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      weight: 70, // default weight
      height: 170, // default height
      bmi: null,
    };
  },
  methods: {
    calculateBMI() {
      this.bmi = (this.weight / (this.height / 100) ** 2).toFixed(2);
    },
  },
  computed: {
    weightStatus() {
      if (this.bmi === null) {
        return ""; // return empty string if bmi is null
      } else if (this.bmi < 18.5) {
        return "Underweight";
      } else if (this.bmi >= 18.5 && this.bmi < 25) {
        return "Normal weight";
      } else if (this.bmi >= 25 && this.bmi < 30) {
        return "Overweight";
      } else if (this.bmi >= 30) {
        return "Obese";
      } else {
        return "";
      }
    },
  },
};
</script>
