<template>
    <div class="container bg-white lg:w-8/12 w-11/12 mx-auto rounded mt-4 pb-5">
      <img src="@/assets/FER-logo.png" alt="FER Logo" class="w-32 mx-auto mt-4" />
      <table class="w-11/12 text-center mt-5 mx-auto">
        <thead>
          <tr>
            <th>Megnevezés</th>
            <th>Megfelelt</th>
            <th>Részben megfelelt</th>
            <th>Nem felelt meg</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item, index) in items" :key="item.id">
            <td class="p-2">{{ item.name }}</td>
            <td
              class="radio-cell"
              :class="{ 'bg-green-200': item.selectedOption === 'Megfelelt' }"
              @click="selectOption(item.id, 'Megfelelt')"
            >
              <input
                type="radio"
                :name="'option-' + item.id"
                value="Megfelelt"
                v-model="item.selectedOption"
                class="custom-radio"
              />
            </td>
            <td
              class="radio-cell"
              :class="{ 'bg-yellow-200': item.selectedOption === 'Részben megfelelt' }"
              @click="selectOption(item.id, 'Részben megfelelt')"
            >
              <input
                type="radio"
                :name="'option-' + item.id"
                value="Részben megfelelt"
                v-model="item.selectedOption"
                class="custom-radio"
              />
            </td>
            <td
              class="radio-cell"
              :class="{ 'bg-red-200': item.selectedOption === 'Nem felelt meg' }"
              @click="selectOption(item.id, 'Nem felelt meg')"
            >
              <input
                type="radio"
                :name="'option-' + item.id"
                value="Nem felelt meg"
                v-model="item.selectedOption"
                class="custom-radio"
              />
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script setup>
  import { ref } from "vue";
  
  const items = ref([
    { id: 1, name: "Megnevezés 1", selectedOption: "" },
    { id: 2, name: "Megnevezés 2", selectedOption: "" },
    { id: 3, name: "Megnevezés 3", selectedOption: "" },
    { id: 4, name: "Megnevezés 4", selectedOption: "" },
    { id: 5, name: "Megnevezés 5", selectedOption: "" },
  ]);
  
  const selectOption = (id, option) => {
    const item = items.value.find((item) => item.id === id);
    item.selectedOption = item.selectedOption === option ? "" : option;
  };
  </script>
  
  <style scoped>
  table {
    width: 100%;
  }
  
  th, td {
    border: 1px solid black;
    padding: 8px;
  }
  
  .radio-cell {
    position: relative;
    padding: 0;
    cursor: pointer;
  }
  
  .radio-cell input[type="radio"] {
    appearance: none;
    width: 20px;
    height: 20px;
    border: 2px solid #555;
    border-radius: 50%;
    display: inline-block;
    margin: 0 auto;
    position: relative;
  }
  
  .radio-cell input[type="radio"]::after {
    content: "";
    width: 12px;
    height: 12px;
    border-radius: 50%;
    background-color: #555;
    display: block;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) scale(0);
    transition: transform 0.2s ease-in-out;
  }
  
  .radio-cell input[type="radio"]:checked::after {
    transform: translate(-50%, -50%) scale(1);
  }
  
  .bg-green-200 {
    background-color: #d1e7dd; 
  }
  
  .bg-yellow-200 {
    background-color: #fff3cd; 
  }
  
  .bg-red-200 {
    background-color: #f8d7da; 
  }
  
  .radio-cell input[type="radio"]:focus {
    outline: none;
  }
  </style>