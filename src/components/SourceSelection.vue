<template>
  <div class="jumbotron">
    <div class="sourceselection">
      <h2><span class="glyphicon glyphicon-list-alt"></span>ESCOGE SourceSelection</h2>
      <select class="form-control" v-on:change="sourceChanged">
        <option v-bind:value="source.id" v-for="source in sources">{{source.name}}</option>
      </select>

      <div v-if="source">
        <h6>{{source.description}}</h6>
        <a v-bind:href="source.url" class="btn btn primary" target="_blank">go to {{source.name}}</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'SourceSelection',
  data () {
    return {
      sources: [],
      source: ''
    }
  },
  methods: {
    sourceChanged (e) {
      for(let i = 0; i < this.sources.length; i ++){
        if(this.sources[i].id === e.target.value){
          this.source = this.sources[i]
        }
      }
      this.$emit('sourceChanged', e.target.value)
    }
  },
  created () {
    this.$http.get('https://newsapi.org/v1/sources?languages=en')
    .then(response => {
      this.sources = response.data.sources
    })
  }
}
</script>

<style lang="css">
</style>
