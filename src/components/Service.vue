<template>
  <v-container>
    <v-card-title>Services</v-card-title>
    <v-form ref="form">
      <v-text-field
        label="Name"
        v-model="serviceObject.serviceName"
        color="green"
      ></v-text-field>
      <v-text-field
        label="Container Name"
        v-model="serviceObject.containerName"
        color="green"
      ></v-text-field>
      <v-text-field
        label="Image"
        v-model="serviceObject.imageName"
        color="green"
        persistent-hint="true"
        hint="Format image:tag"
      ></v-text-field>
      <div class="div" :key="dep" v-for="dep in numberOfDependencies">
        <v-text-field
          label="Depends On"
          v-model="serviceObject.dependsOn[dep - 1]"
          append-icon="mdi-plus-box"
          @click:append="numberOfDependencies++"
          color="green"
        >
        </v-text-field>
      </div>
      <div class="div" :key="env" v-for="env in numberOfEnvironment">
        <v-text-field
          label="Environment"
          v-model="serviceObject.environment[env - 1]"
          append-icon="mdi-plus-box"
          @click:append="numberOfEnvironment++"
          color="green"
          hint="Format key: value"
          persistent-hint="true"
        ></v-text-field>
      </div>
      <div class="div" :key="port" v-for="port in numberOfPorts">
        <v-text-field
          label="Ports"
          v-model="serviceObject.ports[port - 1]"
          append-icon="mdi-plus-box"
          @click:append="numberOfPorts++"
          color="green"
          hint="Format Local Port:Remote Port"
          persistent-hint="true"
        ></v-text-field>
      </div>
      <div class="div" :key="vol" v-for="vol in numberOfVolumes">
        <v-text-field
          label="Volumes"
          v-model="serviceObject.volumes[vol - 1]"
          append-icon="mdi-plus-box"
          @click:append="numberOfVolumes++"
          color="green"
          hint="Format Local Volume: Remove Volume"
          persistent-hint="true"
        ></v-text-field>
      </div>
      <v-btn color="green white--text" @click="add">Add to Compose</v-btn>
      &nbsp;
      <v-btn color="red white--text" @click="clear">Clear</v-btn>
    </v-form>
  </v-container>
</template>

<script>
export default {
  name: "Service",
  data: function() {
    return {
      numberOfDependencies: 1,
      numberOfPorts: 1,
      numberOfVolumes: 1,
      numberOfEnvironment: 1,
      serviceObject: {
        serviceName: "",
        imageName: "",
        containerName: "",
        dependsOn: [],
        environment: [],
        ports: [],
        volumes: [],
      },
    };
  },
  methods: {
    add: function() {
      this.$emit("service-added", this.serviceObject);
    },
    clear: function() {
      var obj = this.serviceObject;
      for (const prop of Object.getOwnPropertyNames(obj)) {
        obj[prop] = "";
      }
      obj["dependsOn"] = [];
      obj["environment"] = [];
      obj["ports"] = [];
      obj["volumes"] = [];
    },
  },
};
</script>

<style></style>
