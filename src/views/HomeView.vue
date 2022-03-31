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
        :items="thegender"
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
        { text: "Država", value: "nationality" },
        { text: "Godine", value: "age" },
        { text: "Spol", value: "gender" },
      ],
    };
  },
  methods: {
    async fetchData(name) {
      let nat = await fetch("https://api.nationalize.io/?name=" + this.name);
      let thenation = await nat.json();
      console.log(thenation)
      let age = await fetch("https://api.agify.io/?name=" + this.name);
      let theage = await age.json();
      console.log(theage)
      let gender = await fetch("https://api.genderize.io/?name=" + this.name);
      let thegender = await gender.json();
      console.log(thegender)

      this.age=theage;
    },
  },
};
</script>
