<template>
  <div class="container bg-white lg:w-8/12 w-11/12 mx-auto rounded mt-4 py-5">
    <img src="@/assets/FER-logo.png" alt="FER Logo" class="w-32 mx-auto" />

    <div class="w-11/12 mx-auto mb-28">
      <select
        v-model="selectedItemsName"
        class="mt-4 border border-gray-300 md:w-5/12 w-10/12 "
      >
        <option value="items">Terület 1</option>
        <option value="items2">Terület 2</option>
        <option value="items3">Terület 3</option>
      </select>
      <table class="text-center mt-5 mx-auto w-full">
        <thead>
          <tr>
            <th class="w-5/12">Megnevezés</th>
            <th class="w-2/12">Megfelelt</th>
            <th class="w-2/12">Részben megfelelt</th>
            <th class="w-2/12">Nem felelt meg</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item, index) in selectedItems" :key="item.id">
            <td class="p-2">{{ item.name }}</td>
            <td
              class="radio-cell"
              :class="{ 'bg-green': item.selectedOption === 'Megfelelt' }"
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
              :class="{
                'bg-yellow': item.selectedOption === 'Részben megfelelt',
              }"
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
              :class="{ 'bg-red': item.selectedOption === 'Nem felelt meg' }"
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

    <div class="signature-section mt-28 flex justify-between w-10/12 mx-auto">
      <div class="signature-block">
        <hr class="w-48 mx-auto" />
        <p class="text-center mt-2">{{ selectedName1 }}</p>
        <select
          v-model="selectedName1"
          class="mt-2 p-2 border border-gray-300 w-full"
        >
          <option v-for="name in names" :key="name" :value="name">
            {{ name }}
          </option>
        </select>
      </div>

      <div class="signature-block">
        <hr class="w-48 mx-auto" />
        <p class="text-center mt-2">{{ selectedName2 }}</p>
        <select
          v-model="selectedName2"
          class="mt-2 p-2 border border-gray-300 w-full"
        >
          <option v-for="name in names" :key="name" :value="name">
            {{ name }}
          </option>
        </select>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        { id: 1, name: "Megnevezés 1", selectedOption: "" },
        { id: 2, name: "Megnevezés 2", selectedOption: "" },
        { id: 3, name: "Megnevezés 3", selectedOption: "" },
        { id: 4, name: "Megnevezés 4", selectedOption: "" },
        { id: 5, name: "Megnevezés 5", selectedOption: "" },
      ],
      items2: [
        { id: 1, name: "Megnevezés 6", selectedOption: "" },
        { id: 2, name: "Megnevezés 7", selectedOption: "" },
        { id: 3, name: "Megnevezés 8", selectedOption: "" },
        { id: 4, name: "Megnevezés 9", selectedOption: "" },
        { id: 5, name: "Megnevezés 10", selectedOption: "" },
      ],
      items3: [
        { id: 1, name: "Megnevezés 11", selectedOption: "" },
        { id: 2, name: "Megnevezés 12", selectedOption: "" },
        { id: 3, name: "Megnevezés 13", selectedOption: "" },
        { id: 4, name: "Megnevezés 14", selectedOption: "" },
      ],
      selectedItemsName: "items",
      names: ["Név 1", "Név 2", "Név 3", "Név 4", "Név 5"],
      selectedName1: "",
      selectedName2: "",
    };
  },
  computed: {
    selectedItems() {
      return this.selectedItemsName === "items"
        ? this.items
        : this.selectedItemsName === "items2"
        ? this.items2
        : this.items3;
    },
  },
  methods: {
    selectOption(id, option) {
      const currentItems = this.selectedItems;
      const item = currentItems.find((item) => item.id === id);
      item.selectedOption = item.selectedOption === option ? "" : option;
    },
  },
};
</script>

<style scoped>
th,
td {
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

.bg-green {
  background-color: green;
}

.bg-yellow {
  background-color: orange;
}

.bg-red {
  background-color: red;
}

.radio-cell input[type="radio"]:focus {
  outline: none;
}

.signature-section {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 20px;
}

@media (max-width: 768px) {
  .signature-section {
    flex-direction: column;
  }

  .signature-block {
    width: 90%; 
    margin-bottom: 16px; 
  }

  .signature-block:last-child {
    margin-bottom: 0; 
  }

  hr {
    width: 90%;
  }
}

.signature-block {
  text-align: center;
}

select {
  padding: 5px;
  font-size: 14px;
  border: 1px solid #ccc;
  border-radius: 4px;
  background-color: #f9f9f9;
  transition: border-color 0.3s ease;
  appearance: none;
}

select:focus {
  border-color: #007bff;
  outline: none;
  box-shadow: 0 0 4px rgba(0, 123, 255, 0.6);
}

select:hover {
  border-color: #007bff;
}

option {
  font-size: 14px;
}

hr {
    border-color: black;
}
</style>
