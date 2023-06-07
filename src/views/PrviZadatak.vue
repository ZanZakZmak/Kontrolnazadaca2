<template>
  <v-container fill-height fluid class="background">
    <v-row>
      <v-col cols="12">
        <v-card class="pa-3" outlined width="600px">
          <v-card-title></v-card-title>
          <v-card-text>
            <v-form>
              <v-text-field v-model="ime" label="ime" outlined></v-text-field>
              <v-text-field
                v-model="prezime"
                label="Prezime"
                outlined
              ></v-text-field>
              <v-text-field
                v-model="brojdolazaka"
                label="Broj dolazaka"
                outlined
              ></v-text-field>
              <v-text-field
                v-model="prviKolokvij"
                label="rezultat prvog"
                outlined
              ></v-text-field>
              <v-text-field
                v-model="drugiKolokvij"
                label="rezultat drugog"
                outlined
              ></v-text-field>
              <v-text-field
                v-model="kontinuiranoPracenje"
                label="kontinuirano pracenje"
                outlined
              ></v-text-field>
            </v-form>
          </v-card-text>
          <v-card-actions>
            <v-btn
              color="black"
              class="white--text"
              elevation="0"
              @click="obrisiSveUnesenePodatke"
            >
              BRISI PODATKE
            </v-btn>
            <v-btn elevation="2" @click="ocistiFormu">Očisti</v-btn>
            <v-btn elevation="2" @click="dodajStudenta">OK</v-btn>
            <v-spacer></v-spacer>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "prvi-zadatak",
  data() {
    return {
      ime: "",
      prezime: "",
      brojdolazaka: "",
      prviKolokvij: "",
      drugiKolokvij: "",
      kontinuiranoPracenje: "",
    };
  },
  watch: {},
  methods: {
    ocistiFormu() {
      (this.ime = ""),
        (this.prezime = ""),
        (this.brojdolazaka = ""),
        (this.prviKolokvij = ""),
        (this.drugiKolokvij = ""),
        (this.kontinuiranoPracenje = "");
    },
    dodajStudenta() {
      let noviStudent = {
        //Dodaj propertyje
        ime: this.ime,
        prezime: this.prezime,
        brojdolazaka: this.brojdolazaka,
        prviKolokvij: this.prviKolokvij,
        drugiKolokvij: this.drugiKolokvij,
        kontinuiranoPracenje: this.kontinuiranoPracenje,
      };
      //ovo ne diraj
      let studenti = JSON.parse(localStorage.getItem("studenti"));
      if (!studenti) {
        studenti = [];
      }
      studenti.push(noviStudent);
      localStorage.setItem("studenti", JSON.stringify(studenti));
      this.ocistiFormu();
    },
    obrisiSveUnesenePodatke() {
      localStorage.clear();
    },
  },
};
</script>
