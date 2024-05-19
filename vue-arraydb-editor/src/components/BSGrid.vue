<template>
    <table class="table table-hover" v-if="items.length != 0">
      <thead>
        <tr>
          <th>ID</th>
          <th>Имя</th>
          <th>Возраст</th>
          <th>Email</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item,index) in items">
          <td>{{ index }}</td>
          <td>{{ item.Name }}</td>
          <td>{{ item.Age }}</td>
          <td>{{ item.Email }}</td>
          <td>
            <button type="button" class="btn btn-primary" @click="onedit(index)">Редактировать</button>&nbsp;
            <button type="button" class="btn btn-danger" data-bs-toggle="modal" data-bs-target="#myModal" @click="onselect(index)">Удалить</button>
          </td>
        </tr>
      </tbody>
    </table>

    <!-- The Modal -->
<div class="modal" id="myModal">
  <div class="modal-dialog">
    <div class="modal-content">

      <!-- Modal Header -->
      <div class="modal-header">
        <h4 class="modal-title">Подтверждение удаления</h4>
        <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
      </div>

      <!-- Modal body -->
      <div class="modal-body">
        Действительно удалить выбранный элемент?        
      </div>

      <!-- Modal footer -->
      <div class="modal-footer">
        <button type="button" class="btn btn-primary" data-bs-dismiss="modal">Нет</button>
        <button type="button" class="btn btn-danger" data-bs-dismiss="modal" @click="ondelete(selected_index)">Да</button>
      </div>

    </div>
  </div>
</div>
</template>

<script>
export default {
    data(){
        return {
            //Индекс выбранного элемента
            //если ничего не выбрано - он равен -1
            selected_index: -1
        }
    },
    //Атрибуты тега компонента
    "props":{
        items: {
            type: Array,
            required: true
        },
        onedit: {
            type: Function,
            required: true
        },
        ondelete: {
            type: Function,
            required: true
        }
    },
    methods: {
      onselect(index){        
        //При нажатии на кнопку "Удалить"
        //получить индекс выбранного элемента
        this.selected_index = index;
      }
    }
}
</script>

<style scoped>

</style>