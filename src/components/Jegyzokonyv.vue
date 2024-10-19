<template>
  <div class="conatiner bg-white w-8/12 mx-auto rounded mt-4">
    <p class="text-center">FER jegyzőkönyv</p>
    <table class="w-full text-center mt-5">
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
          <td>
            <input type="radio" :name="'option-' + item.id" value="Megfelelt" />
          </td>
          <td>
            <input type="radio" :name="'option-' + item.id" value="Részben megfelelt" />
          </td>
          <td>
            <input type="radio" :name="'option-' + item.id" value="Nem felelt meg" />
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { ref } from "vue";

const items = ref([
  { id: 1, name: "Tűzoltókészülék" },
  { id: 2, name: "Megnevezés 2" },
  { id: 3, name: "Megnevezés 3" },
  { id: 4, name: "Megnevezés 4" },
  { id: 5, name: "Megnevezés 5" },
]);
</script>

<style scoped></style>
