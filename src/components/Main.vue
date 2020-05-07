<template>
  <v-container>
    <v-row>
      <v-col>
        <v-card height="100%">
          <v-card-text>
            <Service v-on:service-added="addService" />
          </v-card-text>
        </v-card>
      </v-col>
      <v-col>
        <v-card height="100%" color="black">
          <Compose :newService="newService" />
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import Service from "./Service";
import Compose from "./Compose";

export default {
  name: "Services",
  components: {
    Service,
    Compose,
  },
  data: function() {
    return {
      newService: {},
    };
  },
  methods: {
    addService: function(data) {
      this.newService = Object.assign({}, data);
    },
  },
};
</script>

<style scoped></style>
