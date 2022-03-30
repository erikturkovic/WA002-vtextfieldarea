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
      <v-btn rounded color="primary" dark> OK </v-btn>
      <v-data-table
        :headers="headers"
        :items="desserts"
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
          value: "",
        },
        { text: "Države", value: "drzave" },
        { text: "Godine", value: "godine" },
        { text: "Spol", value: "spol" },
      ],
    };
  },

  async mounted() {
    let fecnatio = await fetch("https://api.nationalize.io/?name=" + this.name);
    let fecage = await fetch("https://api.agify.io/?name=" + this.name);
    let fecgender = await fetch("https://api.genderize.io/?name=" + this.name);

    let thenation = await fecnatio.json();
    let theage = await fecage.json();
    let thegender = await fecgender.json();

    console.log(nation);
    console.log(age);
    console.log(gender);

    this.nation = thenation;
    this.age = theage;
    this.gender = thegender;
  },
};
</script>
