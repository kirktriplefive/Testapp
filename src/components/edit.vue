<template>
    <form @submit.prevent="onSubmit">
        <div>Имя автора<input type="text"  v-model="name">{{this.name}}</div>
        <div>Год написания<input type="number"  v-model="year">{{this.year}}</div>
        <div>Название книги<input type="text"  v-model="naz">{{this.naz}}</div>
        <div>Количество страниц<input type="number"  v-model="kol">{{this.kol}}</div>
        
        
        <button type="submit" >Добавить в библиотеку</button>
    </form>
</template>
<script >
import spisok from '@/components/liiiil'
  export default{
      data() {
          return{
                name:'',
                year:'',
                naz:'',
                kol:''
          }
      },
      methods:{
          onSubmit() {
              if (this.name.trim() && this.naz.trim() && this.kol >0 && this.year <2021 && this.year >0 ) {
                  const newlib = {
                      id: Date.now(),
                      name: this.name,
                      year: this.year,
                      naz: this.naz,
                      kol: this.kol

                  }
              
               
                  
                  this.$emit('edit-lib', newlib)
                  this.name = ''
                  this.year = ''
                  this.naz = ''
                  this.kol = ''
              }
               else { 
                    alert( 'Вы не ввели одно из значений' )
                    this.name = ''
                    this.year = ''
                    this.naz = ''
                    this.kol = ''

                }

          }
      },
      components: {
            spisok
        }
  }
</script>

<style scoped>
</style>
