<template>
  <v-layout>
    <v-container fluid>
      <v-row justify="space-between">
        <ServiceStatus status-url="https://hs1storage.blob.core.windows.net/servicestatus/soeconnect_status.json" />
        <ServiceStatus status-url="https://hs1storage.blob.core.windows.net/servicestatus/ascend_status.json" />
        <ServiceStatus status-url="https://hs1storage.blob.core.windows.net/servicestatus/wavelength_status.json"/>
      </v-row>
    </v-container>
  </v-layout>
</template>

<script>
import ServiceStatus from '~/components/ServiceStatus.vue'

export default {
  components: {
    ServiceStatus
  }
}
</script>
