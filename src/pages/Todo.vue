<template>
  <div>
    <div>
      <HelloWorld :message="fullName" @add="addToDo">
        <template slot="greeting">Hello</template>
      </HelloWorld>
    </div>
    <div>
      Firstname : <input type="text" v-model="firstName">
    </div>
    <div>
      Lastname : <input type="text" v-model="lastName">
    </div>
    <div>
      Fullname : {{fullName}}
    </div>
    <List />
    <button @click="test">Go to test</button>
  </div>
</template>

<script>

import HelloWorld from '@/components/HelloWorld'
import List from '@/components/List'
import { mapActions } from 'vuex'
export default {
  name: 'Todo',
  data () {
    return {
      firstName: '',
      lastName: ''
    }
  },
  computed: {
    fullName () {
      return `${this.firstName} ${this.lastName}`
    }
  },
  watch: {
    firstName (newValue, oldValue) {
      // console.log('newValue = ' + newValue)
      // console.log('oldValue = ' + oldValue)
    }
  },
  methods: {
    ...mapActions({
      setList: 'setList'
    }),
    addToDo (name) {
      this.setList(name)
    },
    test () {
      this.$router.push({name: 'Test', params: { id: 100 }})
    }
  },
  components: {
    HelloWorld,
    List
  },
  created () {
    console.log('created working ...')
  },
  mounted () {
    console.log('mounted working ...')
  }
}
</script>

<style scoped>

</style>
