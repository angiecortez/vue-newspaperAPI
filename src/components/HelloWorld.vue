<template>
  <div class="container">
    <SourceSelection v-on:sourceChanged="sourceChanged"></SourceSelection>
    <NewsLists v-bind:source="source"></NewsLists>
  </div>
</template>

<script>
import SourceSelection from './SourceSelection'
import NewsLists from './NewsLists'
export default {
  name: 'HelloWord',
  components: {
    SourceSelection,
    NewsLists
  },
  data () {
    return {
      source: '',
    }
  },
  methods: {
    sourceChanged (source) {
      this.source = source
    }
  }
}
</script>

<style>
  padding-top: ""
</style>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
