<template>
  <v-layout>
    <v-container fluid>
      <v-row justify="space-between">
        <v-alert class="healthyService" dense outlined type="success">
          Apollo
        </v-alert>
        <v-alert class="healthyService" dense outlined type="success">
          SOEPAY
        </v-alert>
        <v-alert class="degradedService" dense outlined type="success">
          NHS
        </v-alert>
        <v-alert class="unhealthyService" dense outlined type="error">
          SOEConnect
        </v-alert>
      </v-row>
    </v-container>
  </v-layout>
</template>
