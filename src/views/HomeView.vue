<template>
  <v-form>
    <v-container>
      <v-row>
        <v-col cols="12" sm="5">
          <v-text-field
            v-model="name"
            label="Upiši ime"
            single-line
            outlined
          ></v-text-field>
        </v-col>
      </v-row>
      <v-btn rounded color="primary" dark @click="fetchData()"> OK </v-btn>
      <v-data-table
        :headers="headers"
        :items="placeholder"
        :items-per-page="1"
        class="elevation-1"
      ></v-data-table>
    </v-container>
  </v-form>
</template>

<script>
export default {
  data() {
    return {
      nation: [],
      age: [],
      gender: [],
      name: [],

      headers: [
        {
          text: "Ime",
          align: "start",
          sortable: false,
          value: "name",
        },
        { text: "Država", value: "country" },
        { text: "Vjerojatnost države", value: "probability of country" },
        { text: "Godine", value: "age" },
        { text: "Spol", value: "gender" },
        { text: "Vjerojatnost spola", value: "probability of gender" },
      ],
    };
  },
  methods: {
    async fetchData(name) {
      let thenation = await fetch("https://api.nationalize.io/?name=" + this.name);
      let nation = await thenation.json();
      console.log(nation);
      let theage = await fetch("https://api.agify.io/?name=" + this.name);
      let age = await theage.json();
      console.log(age);
      let thegender = await fetch("https://api.genderize.io/?name=" + this.name);
      let gender = await thegender.json();
      console.log(gender);     
       
    },
  },
};
</script>
