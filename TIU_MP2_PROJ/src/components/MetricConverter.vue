 <script setup> //Composition API
import Swal from 'sweetalert2';
import 'sweetalert2/dist/sweetalert2.min.css';
import {ref, computed
} from 'vue';

const meterInputValue = ref(0);
const gramInputValue = ref(0);
const celciusInputValue = ref(0);

const showAlert = (message, icon = 'success') =>{
    Swal.fire({
      title: 'Metric Converter',
      text: message,
      icon: icon,
      confirmButtonText: 'OK',
    })
  }
  const convert = () => { 
    if (!this.meterInputValue && !this.gramInputValue && !this.celciusInputValue && !this.secondsInputValue) 
      this.showAlert('Please enter a value for conversion.', 'error');
      return;
    }

//m to ft formula
const feetConvertedValue = computed(() => meterInputValue.value *3.28084);
const showAlertMToFT = () => {
if (!meterInputValue.value) {
  showAlert('Please enter a value for conversion.', 'error');
  return;
}
showAlert(`Conversion: ${meterInputValue.value} meters to ${feetConvertedValue.value.toFixed(3)} feet`);
};

//g to kg formula
const kilogramConvertedValue = computed(() => gramInputValue.value / 1000);
const showAlertGToKG = () => {
if (!gramInputValue.value) {
  showAlert('Please enter a value for conversion.', 'error');
  return;
}
showAlert(`Conversion: ${gramInputValue.value} grams to ${kilogramConvertedValue.value.toFixed(3)} kilograms`);
};

//C to F formula
const fahrenheitConvertedValue = computed (() => (celciusInputValue.value * 9/5) +32);
const showAlertCToF = () => {
  if (!celciusInputValue.value) {
    showAlert('Please enter a value for conversion.', 'error');
    return;
  }
  showAlert(`Conversion: ${celciusInputValue.value} Celsius to ${fahrenheitConvertedValue.value.toFixed(2)} Fahrenheit`);
};

</script>

<template>
  <main>
  <!-- Header -->
  <header class="bg-blue-500 text-white text-center py-6">
    <h1 class="text-4xl font-semibold">Metric Converter</h1>
  </header>

  <!-- Metric Converter -->
  <div class="flex items-center center h-screen bg-aqua-200" style="width: 100%;">
    <div class="container m-72">
        
      <!-- m to ft -->
      <div class="mToft">
        <div>
          <!-- user input to enter values -->
          <label class="block mb-1">Enter value in meters:</label>
          <input v-model="meterInputValue" type="number" class="border p-2 w-full" />
        </div>

        <!-- Button for m to ft conversion -->
        <button @click="showAlertMToFT" class="bg-blue-500 text-white p-2 mt-4">Convert to feet</button>
      </div>

    
      <!-- g to kg -->
      <div class="grid gap-2 mt-5">
        <div class="gTokg">
          <div>
            <!-- user input to enter values -->
            <label class="block mb-1">Enter value in grams:</label>
            <input v-model="gramInputValue" type="number" class="border p-2 w-full" />
          </div>

          <!-- Button for g to kg conversion -->
          <button @click="showAlertGToKG" class="bg-blue-500 text-white p-2 mt-4">Convert to kilograms</button>
        </div>
      </div>

        <!-- C to F -->
        <div class="grid gap-4 mt-5">
          <div class="cTof">
            <div>
              <!-- user input to enter values -->
              <label class="block mb-1">Enter Celsius value:</label>
              <input v-model="celciusInputValue" type="number" class="border p-2 w-full" />
            </div>

          <!-- Button for C to F conversion -->
          <button @click="showAlertCToF" class="bg-blue-500 text-white p-2 mt-4">Convert to Fahrenheit</button>
          </div>
        </div>    
    </div>
  </div>
    
    <!-- Footer -->
    <footer class="flex justify-between items-center 
    text-white text-center py-8 mt-10" >
      <div class="text-left pl-6">
        <p>Tiu, Shane Ivan M.</p>
        <p>4ITC - IT ELEC4C</p>
      </div>

      <div class = "text-left pl-2">
        <p>&copy; 2024 Metric Converter</p>
      </div>
    </footer>
  </main>
</template>

<style scoped>
main {
  background-color: #679289;
}

header {
  background-color: #003554;
  font-family: Cambria, Cochin, Georgia, Times, 'Times New Roman', serif;
}

.mToft {
  background-color: #fffaca;
  padding: 1rem;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.gTokg {
  background-color: #fffaca;
  padding: 1rem;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.cTof {
  background-color: #fffaca;
  padding: 1rem;
  border-radius: 8px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

footer {
  background-color: #2C3E50;
}
</style>