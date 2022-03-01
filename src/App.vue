<template>
  <div id="app">
    <div style="margin: 30px 0;">
      <input type="text" v-model="inputPerson.name" placeholder="Naam" />
      <input type="text" v-model="inputPerson.title" placeholder="Titel" />
      <input type="text" v-model="inputPerson.phone" placeholder="Phone" />
    </div>
    <Signature :person="inputPerson" />
    <Signature v-for="(person, i) in data" :key="i" :person="person" />
  </div>
</template>

<script>
import data from "./data.js";
import Signature from "@/Signature";

export default {
  name: 'App',
  components: {Signature},
  data: function () {
    return {
      inputPerson: {
        name: null,
        phone: null,
        title: null
      },
      data: data,
    }
  },
  methods: {
  }
}
</script>
