<template>
  <div id="app">
      <h1> Библиотека </h1>
        <hr />
        <div>
        <div class="left_block">
        <add id="table"
          @add-lib="addlib"
        />
        </div>
        <div class="right">
        <libr if
           v-if="librir.length"
           v-bind:librir="librir"
           @remove-lib="removelib"
           @edit-lib="editLib"
         />
         <p v-else> Библиотека пуста </p>
         </div>
         </div>
  </div>
</template>

<script>
 import libr from '@/components/libr'
 import add from '@/components/add'
 import edit from '@/components/edit'
export default {
  name: 'App',
   data() { 
            return {
                librir:[],
                errors: []
            }
        },
          mounted() {
      if (localStorage.getItem('librir')) {
      try {
        this.librir = JSON.parse(localStorage.getItem('librir'));
      } catch(e) {
        localStorage.removeItem('librir');
      }
    }
          },
    methods:{
      addlib(lib) {
        if (this.name &&  this.year && this.naz && this.kol) {
        return true;
      }
        this.librir.push(lib);
        this.saveLib();
      },
      removelib(id) {
        this.librir = this.librir.filter(t => t.id !== id)
        this.librir.splice(id, 1);
        this.saveLib();
      },
      saveLib() {
      const parsed = JSON.stringify(this.librir);
      localStorage.setItem('librir', parsed);
    }, 
    editLib(id) {
      x=this.lib
      this.removelib(id)
      c=1;
    }  
    },
        components: {
            libr: libr,
            add,
            edit
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
#table {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
}
.left_block {
float:left;
width: 200px;
}
.right {
width: 200px;
float:left;
}
@media handheld {
 .right {
 } 
  
}



</style>
