<script>
export default {
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
  }
}
</script>

<template>
  <div class="notecard" v-bind:id="note.urgensy">
    <h1>{{ note.title }}</h1>
    <p>{{ note.text }}</p>
    <p>{{ note.date }}</p>
    <p>{{ note.urgensy }}</p>
    <button class="delete_note" @click="deletenote(index)"> Выполненно </button>
  </div>
  <!--  <p>{{ element.text }}</p>-->

</template>

<style scoped>
.notecard {
  background: #9de1b4;
  border: 1px #c5e7bf solid;
  border-radius: 10px 10px 10px 0;
  margin: 20px;
}
.delete_note {
  background: #d9534f;
  border: 1px #d9534f solid;
  border-radius: 10px 10px 10px 0;
}
#Extra{
  background: red;
}
#Middle{
  background: yellow;
}
</style>