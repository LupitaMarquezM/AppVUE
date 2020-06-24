<template>
  <div>
    <List :elements-list="elements" />
  </div>
</template>

<script>


export default {
  components: {
    
  },
  created() {
    this.findAll();
  },
  data() {
    return {
      elements: []
    };
  },
  methods: {
    findAll: function() {
      fetch('http://127.0.0.1:8000/api/category/'+this.$route.params.id+'?format=json')
          this.$route.params.id +
          "/elements/?format=json"
      
        .then(res => res.json())
        .then(res => (this.elements = res));
    }
  },
  watch: {
    "$route.params.id": function() {
      console.log("Listado de categorías");
      this.findAll();
    }
  }
};
</script>

<style >
.box {
  border: 3px solid #ccc;
  margin: 5px 0 0 0;
}
</style>