<template>
    <div class="container">
      <br/>
      <BSForm modalid="mymodal" :item="user" :onsave="onsave" :onadd="onadd"/> 
      <br/><br/>   
      <BSGrid :items="users" :onedit="onedit" :ondelete="ondelete"/>
    </div>
</template>

<script>
import bootstrap from 'bootstrap/dist/js/bootstrap.bundle.js'
import BSForm from './components/BSForm.vue'
import BSGrid from './components/BSGrid.vue'
export default {
  //Перечисление компонентов, подключенных к данному компоненту
  components: {BSForm,BSGrid},
  //Данные (model) данного компонента
  data(){
    return {
      users: [], //Данные таблицы
      user: {}, //Данные формы
      is_edit: false //Флаг редактирования
    };
  },
  methods: {
    onsave(){
      //При нажатии на кнопку "Сохранить"
      //в диалоговом окне     

      if(!this.is_edit) //Если НЕ установлен флаг редактирования 
        //создание нового элемента
        this.users.push({           
          Name: this.user.Name,
          Age: this.user.Age,
          Email: this.user.Email
        });
      else { //Иначе
        //редактирование существующего элемента
        this.users[this.user.index]=Object.assign({},this.user);
        this.is_edit=false; //сброс флага редактирования
      }   
    },
    onadd(){
      //При нажатии на кнопку "Создать"

      //сброс флага редактирования
      this.is_edit=false; 
      //инициализация пустым значением объекта, привязанного к диалоговому окну
      this.user = {}; 
    },
    onedit(index){
      //При нажатии на кнопку "Редактировать" в таблице 

      //установить флаг редактирования
      this.is_edit=true;
      //получение редактируемого элемента из таблицы
      //и присвоение его объекту формы      
      this.user = Object.assign({},this.users[index]);
      //this.user = this.users[index];   
      this.user.index = index;
      //открытие диалогового окна формы
      let myModal = new bootstrap.Modal(document.getElementById('mymodal'), {});
      myModal.show(); 
    },
    ondelete(index){
      //При нажатии на кнопку "Удалить" в таблице  (точнее -
      //при нажатии на кнопку "Да" в диалоговом окне подтверждения удаления)
      
      //удаление выбранного элемента
      this.users.splice(index,1);
    }
  }}
</script>

<style scoped>

</style>
