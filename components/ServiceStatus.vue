<template>
  <v-tooltip bottom>
    <template v-slot:activator="{ on }">
      <div v-on="on">
        <v-icon v-if="compact" :color="color">
          {{ icon }}
        </v-icon>
        <v-alert v-else dense outlined :type="alertType">
          {{ info.name }}
        </v-alert>
      </div>
    </template>
    <table>
      <tr>
      {{ info.name }} - <b>{{ info.status }}</b>
      </tr>
      <tr>
        {{ info.description }}
      </tr>
    </table>
  </v-tooltip>
</template>

<script>
import axios from 'axios'

export default {
  props: {
    statusUrl: {
      type: String,
      required: true
    },
    compact: Boolean
  },
  data() {
    return {
      info: {
        status: '',
        name: '',
        description: ''
      }
    }
  },
  computed: {
    alertType() {
      switch (this.info.status) {
        case 'Healthy':
          return 'success'
        case 'Unhealthy':
          return 'error'
        default:
          return 'warning'
      }
    },
    color() {
      switch (this.info.status) {
        case 'Healthy':
          return 'green'
        case 'Unhealthy':
          return 'red'
        default:
          return 'orange'
      }
    },
    icon() {
      switch (this.info.status) {
        case 'Healthy':
          return 'mdi-checkbox-marked-circle'
        case 'Unhealthy':
          return 'mdi-minus-circle'
        default:
          return 'mdi-alert'
      }
    }
  },
  // eslint-disable-next-line
  mounted: function() {
    return axios
      .get(this.statusUrl)
      .then((response) => {
        console.log(response.data)
        this.info = {
          status: response.data.Status,
          name: response.data.Name,
          description: response.data.Details
        }
      })
      .catch(function(error) {
        // handle error
        console.log(error)
      })
  }
}
</script>
