<template>
    <!-- Button to Open the Modal -->
    <button type="button" class="btn btn-primary" data-bs-toggle="modal" :data-bs-target="'#'+modalid" @click="onadd()">
    Создать
    </button>

    <!-- The Modal -->
<div class="modal" :id="modalid">
  <div class="modal-dialog">
    <div class="modal-content">

      <!-- Modal Header -->
      <div class="modal-header">
        <h4 class="modal-title"></h4>
        <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
      </div>

      <!-- Modal body -->
      <div class="modal-body">
        <div class="mb-3 mt-3">
        <label for="name" class="form-label">Имя:</label>
        <input v-model="item.Name" type="text" class="form-control" id="name" placeholder="Введите имя" name="name">
      </div>
      <div class="mb-3">
        <label for="age" class="form-label">Возраст:</label>
        <input v-model="item.Age" type="text" class="form-control" id="age" placeholder="Введите возраст" name="age">
      </div>
      <div class="mb-3">
        <label for="email" class="form-label">Email:</label>
        <input v-model="item.Email" type="text" class="form-control" id="email" placeholder="Введите email" name="email">
      </div>
  
      </div>

      <!-- Modal footer -->
      <div class="modal-footer">
        <button type="button" class="btn btn-primary" data-bs-dismiss="modal" @click="onsave()">Сохранить</button>
        <button type="button" class="btn btn-danger" data-bs-dismiss="modal">Отмена</button>
      </div>

    </div>
  </div>
</div>
    
</template>

<script>
export default {
    //Атрибуты тега компонента    
    "props":{
        modalid: {
          type: String,
          required: true
        },
        item: {
            type: Object,
            required: true
        },
        onsave: {
            type: Function,
            required: true
        },
        onadd: {
            type: Function,
            required: true
        }        
    }
}
</script>

<style scoped>

</style>