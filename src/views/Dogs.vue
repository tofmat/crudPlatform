<template>
    <div>
      <petTable
        species= "dogs"
        :pets="dogs"
      />
    </div>
</template>

<script>
/* eslint-disable */
import petTable from '@/components/petTable.vue'


import { mapState } from 'vuex'
export default {
    components: {
        petTable
    },
  data () {
    return { 
    }
  },
  computed: {
    ...mapState([
       'dogs' 
    ])
  }
}
</script>
