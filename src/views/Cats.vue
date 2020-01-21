<template>
    <div>
      <petTable
        species= "cats"
        :pets="cats"
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
       'cats'
    ])
  }
}
</script>
