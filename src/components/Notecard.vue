<script>
export default {
  data(){
    return {
      dateTime: ''
    }
  },
  props: {
    note: {
      type: Object,
      required: true
    },
    index: {
      type: Number,
      required: true
    },
    deletenote:{
      type: Function,
      required: true
    }
  },
  methods: {
    formatDate(date) {
      const year = date.getFullYear();
      const month = (date.getMonth() + 1).toString().padStart(2, '0');
      const day = date.getDate().toString().padStart(2, '0');
      const hours = date.getHours().toString().padStart(2, '0');
      const minutes = date.getMinutes().toString().padStart(2, '0');

      this.dateTime = `${year}-${month}-${day}T${hours}:${minutes}`;
    }
  }
}
</script>

<template>
  <div class="notecard" v-bind:id="note.urgensy">
    <div class="notecard-header">
    <h1>Название: {{ note.title }}</h1>
    <br>
    <p>Описание: {{ note.text }}</p>
      <p>Дата создания: {{ note.curDate}}</p>
    <p>Дата: {{ note.date}}</p>
    </div>
    <button class="delete_note" @click="deletenote(index)"> Выполненно </button>
  </div>
  <!--  <p>{{ element.text }}</p>-->

</template>

<style scoped>
.notecard {
  display: flex;
  justify-content: space-between;
  width: 350px;
  height: 200px;
  background: #39E64E;
  border: 1px #69F37A solid;
  border-radius: 10px;
  margin: 20px;
  transition: all 500ms ease;
}
.notecard:hover {
  transform: scale(1.02);
}
.delete_note {
  background: #7049DD;
  border: 1px #7049DD solid;
  border-radius: 10px;
  transition: all 500ms ease;
}
.delete_note:hover {
  transform: scale(0.97);
}
#Extra{
  background: #FF483F;
}
#Middle{
  background: #FFE03F;
}
</style>