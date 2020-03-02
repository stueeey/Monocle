<template>
  <v-layout>
    <v-container fluid>
      <v-row justify="space-between">
        <ServiceStatus status="healthy">Apollo</ServiceStatus>
        <ServiceStatus status="degraded">HS1Pay</ServiceStatus>
        <ServiceStatus status="unhealthy">HS1Connect</ServiceStatus>
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
