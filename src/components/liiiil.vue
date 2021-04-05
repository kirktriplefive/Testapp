<template>
  <table id="right">
  <colgroup>
    <col span="5" style="background:Khaki"><!-- С помощью этой конструкции задаем цвет фона для первых двух столбцов таблицы-->
  </colgroup>
  <tr>
    <th>№ п/п</th>
    <th>Имя</th>
    <th>Год</th>
    <th>Название</th>
    <th>Количество страниц</th>
    <th></th>
  </tr>
  <tr>
    <td>{{index + 1}}</td>
    <td>{{lib.name}}</td>
    <td>{{lib.year}}</td>
    <td>{{lib.naz}}</td>
    <td>{{lib.kol}}</td>
    <td>
      <button class="rm" 
        v-on:click="$emit('remove-lib', lib.id)">&times;
      </button>
      <button  
        v-on:click="$emit('edit-lib', lib.id)"> ✎
      </button>
    </td>
  </tr>
 
</table>
</template>

<script>
export default {
    props: {
        lib: {
            type:Object,
            reqired: true
        },
        index: Number
    }
    
}
</script>

<style scoped>
#right {
  float:left;
  width: 10%;

}
@media handheld {
 #right{
  width: 5%;
 } 
  
  
}
</style>