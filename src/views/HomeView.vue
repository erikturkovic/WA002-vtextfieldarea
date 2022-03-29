<template>
  <v-form>
    <v-container>
      <v-row>
        <v-col cols="12" sm="5">
          <v-text-field label="Upiši ime" single-line outlined></v-text-field>
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
      headers: [
        {
          text: "Ime",
          align: "start",
          sortable: false,
          value: "ime",
        },
        { text: "Države", value: "drzave" },
        { text: "Godine", value: "godine" },
        { text: "Spol", value: "spol" },
        { text: "Vjerojatnost", value: "vjerojatnost" },
      ],
    };
  },
};
</script>
