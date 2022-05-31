<template>
  <div id="app">
    <div style="background-color: #898585; padding: 20px; margin-botom: 80px; color: white; font-family: Verdana; font-size: 0.875rem;">
      <h2>Instructies</h2>
      <p>Bij het kopiëren en plakken, zorg ervoor dat je zeker het blokje voor & na de handtekening mee copy paste. (zie screenshot hieronder).</p>
      <img src="https://www.o2o.be/app/uploads/2022/03/Screen-Shot-2022-03-02-at-11.43.00.png" style="max-height: 150px;" />
      <p>Op deze manier ziet de handtekening er op alle devices optimaal uit.</p>
    </div>

    <div style="margin: 30px 0;">
      <input type="text" v-model="inputPerson.name" placeholder="Naam" />
      <input type="text" v-model="inputPerson.title" placeholder="Titel" />
      <input type="text" v-model="inputPerson.phone" placeholder="Phone" />
      <input type="text" v-model="inputPerson.img" placeholder="Image url (wordpress upload)" />
    </div>
    <Signature :person="inputPerson" />
    <Signature v-for="(person, i) in data" :key="i" :person="person" :html="true" />
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
        title: null,
        img: null
      },
      data: data,
    }
  },
  methods: {
  }
}
</script>
