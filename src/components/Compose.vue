<template>
  <v-container>
    <v-card-title class="white--text">Compose File</v-card-title>
    <v-card-text class="white--text" v-if="serviceList.length > 0">
      <strong style="color:white">
        version: '3'
      </strong>
      <v-list :key="serv" v-for="serv in serviceList" color="green--text" dark>
        <div class="serviceName">
          <strong>service:</strong>
          {{ serv.serviceName }}
        </div>
        <div class="serviceAttributes">
          <strong>container_name:</strong>
          {{ serv.containerName }} <br />
          <strong>image:</strong>
          {{ serv.imageName }} <br />
          <div v-if="serv.dependsOn.length > 0">
            <strong>
              depends_on:
            </strong>
            <div
              class="sublist"
              :key="dep"
              v-for="dep in serv.dependsOn"
              style="color:white"
            >
              - {{ dep }}
            </div>
          </div>
          <div v-if="serv.environment.length > 0">
            <strong>
              environment:
            </strong>
            <div
              class="sublist"
              :key="env"
              v-for="env in serv.environment"
              style="color:white"
            >
              - {{ env }}
            </div>
          </div>
          <div v-if="serv.ports[0]">
            <strong>ports:</strong>
            <div
              class="sublist"
              :key="port"
              v-for="port in serv.ports"
              style="color:white"
            >
              - {{ port }}
            </div>
          </div>
          <div v-if="serv.volumes.length > 0">
            <strong>volumes:</strong>
            <div
              class="sublist"
              :key="vol"
              v-for="vol in serv.volumes"
              style="color:white"
            >
              - {{ vol }}
            </div>
          </div>
        </div>
      </v-list>
    </v-card-text>
  </v-container>
</template>

<script>
export default {
  name: "Compose",
  props: {
    newService: Object,
  },
  data: function() {
    return {
      serviceList: [],
    };
  },
  watch: {
    newService() {
      this.serviceList.push(this.newService);
    },
  },
};
</script>

<style>
.serviceAttributes {
  padding-left: 30px;
}

.sublist {
  padding-left: 34px;
  color: white;
}
</style>
