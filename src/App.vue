<template>
  <div id="app">
    <Tablazat :rows="rows"
    @row_added="Added"
    @row_changed="Changed"
    @row_deleted="Deleted"/>
  </div>
</template>

<script>
import Tablazat from './components/Tablazat.vue'

export default {
  name: 'App',
  components: {
    Tablazat
  },
  data() {
    return {
      rows: [
        {
          title: 'Kerék',
          price: 100,
          quantity: 12
        },
        {
          title: 'Teleszkóp',
          price: 1000,
          quantity: 300
        },
        {
          title: 'Kormány',
          price: 230,
          quantity: 5
        },
        {
          title: 'Ajtó',
          price: 45120,
          quantity: 321
        },
      ]
    }
  },
  methods: {
    Added(e) {
      this.rows.push(e)
    },
    Changed(e) {
      this.rows.map((row)=> {
        if (row.title != e.original.title || row.price != e.original.price || row.quantity != e.original.quantity) {
          return row;
        }
        else {
          row.title = e.new.title
          row.price = e.new.price
          row.quantity = e.new.quantity
          return row;
        }
      })
    },
    Deleted(e) {
      this.rows = this.rows.filter((row)=>e.original != row)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
