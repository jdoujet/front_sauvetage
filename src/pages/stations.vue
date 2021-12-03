<template>
  <div id="main" style="background-color: #0e0e0e">
    <div class="center mt-15">
      <v-col cols="12" sm="12" md="8" lg="8" xl="8">
        <v-card style="border: 5px solid; margin: 14% 14% 14% 14%; background-color:#c5c8c9">
          <v-row justify="center">
            <v-col cols="8" sm="8" md="8" lg="8" xl="8">
              <v-select
                v-model="select"
                :items="items"
                item-text="value"
                item-value="url"
                label="Select"
                persistent-hint
                return-object
                single-line
                color="white"
                
              ></v-select>
              <v-text-field v-model="inputValue"></v-text-field>
              </v-col>
            
            
          </v-row>
          <v-row justify="center" style="margin-bottom:3%">
            <v-col cols="4" sm="5" md="5" lg="5" xl="5" >
                <v-btn v-on:click="getArticles" rounded small >Rechercher article</v-btn>
            </v-col>
          </v-row>
<!--           <v-row justify="center">
            
          </v-row> -->
        </v-card>
      </v-col>
    </div>

    <v-simple-table v-if="articles.length > 0">
      <template v-slot:default>
        <thead>
          <tr>
            <th class="text-left">Title</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in articles" :key="item.name">
            <td>{{ item.title }}</td>
          </tr>
        </tbody>
      </template>
    </v-simple-table>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "createStation",

  mounted() {},

  data() {
    return {
      select: { url: "by/boat/name", value: "Par bateau" },
      items: [
        { url: "by/boat/name", value: "Par bateau" },
        { url: "by/title/name", value: "Par titre" },
        { url: "by/savior/name", value: "Par sauveteur" },
      ],

      inputValue: "",
      articles: [],
    };
  },
  methods: {
    getArticles: function () {
      axios
        .get(
          "https://crise-interstellaire-back-end.herokuapp.com/articles/" +
            this.select.url +
            "/" +
            this.inputValue
        )
        .then((response) => (this.articles = response.data));
    },
  },
};
</script>

<style>
:root {
  --main-purple-color: blue;
}
.stationsPageTitle {
  font-size: 25px;
  color: var(--main-purple-color);
}

.v-application .blue--text.text--darken-2 {
  color: var(--main-purple-color) !important;
  caret-color: var(--main-purple-color) !important;
}

#actionMenu {
  padding: 1rem;
  margin: 1rem;
}
</style>