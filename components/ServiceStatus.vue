<template>
  <v-tooltip bottom>
    <template v-slot:activator="{ on }">
      <div v-on="on">
        <v-icon v-if="compact" :color="color">
          {{ icon }}
        </v-icon>
        <v-alert v-else dense outlined :type="alertType">
          <slot></slot>
        </v-alert>
      </div>
    </template>
    <span>
      <slot></slot> - <b>{{ status }}</b>
    </span>
  </v-tooltip>
</template>

<script>
export default {
  props: {
    status: {
      type: String,
      required: true
    },
    compact: Boolean
  },
  data() {
    return {}
  },
  computed: {
    alertType() {
      switch (this.status) {
        case 'healthy':
          return 'success'
        case 'unhealthy':
          return 'error'
        default:
          return 'warning'
      }
    },
    color() {
      switch (this.status) {
        case 'healthy':
          return 'green'
        case 'unhealthy':
          return 'red'
        default:
          return 'orange'
      }
    },
    icon() {
      switch (this.status) {
        case 'healthy':
          return 'mdi-checkbox-marked-circle'
        case 'unhealthy':
          return 'mdi-minus-circle'
        default:
          return 'mdi-alert'
      }
    },
  }
}
</script>
