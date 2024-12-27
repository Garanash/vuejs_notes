<script>
export default {
  data() {
    return {
      placeholderString: 'Введите название заметки',
      title: 'Новая заметка',
      userNoteTitle: '',
      userNotes: '',
      userUrgency: '',
      userDate: Date(),
      notes: []
    }
  },
  methods: {
    CreateNote(note) {
      if (this.userNoteTitle.length > 0 && this.userNotes.length > 0 && this.userDate && this.userUrgency) {
        this.notes.push([
          this.userNoteTitle,
          this.userNotes,
          this.userDate,
          this.userUrgency
        ])
        this.userNoteTitle = ''
        this.userNotes = ''
        this.userDate = Date(1)
        this.userUrgency = ''
      }
    }
  }
}
const App = {}
</script>

<template>
  <div class="container" style="align-content: center; align-items: center; margin: auto">
    <div class="card">
      <h1>{{ title }}</h1>
      <div class="form-control" style="display: flex; flex-direction: column;">
        <label>Введите название заметки</label>
        <input type="text" v-model="userNoteTitle" placeholder="Введите название заметки"/>
        <label>Введите текст заметки</label>
        <textarea v-model="userNotes" placeholder="Введите текст заметки"></textarea>
        <label>Введите дату до которой нужно выполнить задачу</label>
        <input type="datetime-local" v-model="userDate" placeholder="введите дедлайн"/>
        <div class="btn-group">
          <span class="radio_head" id="extras"><label for="one">Срочно</label><input type="radio" id="one" value="Extra"
                                                                                     v-model="userUrgency"/></span>
          <span class="radio_head" id="middlas"><label for="two">Средне</label><input type="radio" id="two"
                                                                                      value="Middle"
                                                                                      v-model="userUrgency"/></span>
          <span class="radio_head" id="lazys"><label for="three">Неважно</label><input type="radio" id="three"
                                                                                       value="EASY"
                                                                                       v-model="userUrgency"/></span>
        </div>
        <button class="btn" type="submit" @click="CreateNote($event.target.value)">Создать заметку</button>
      </div>
    </div>
  </div>
  <div v-for="(el, i) in notes" :key="i">
    <p>{{ el }}</p>
  </div>
</template>

<style scoped>
* {
  font-family: 'Montserrat', sans-serif;
  font-weight: bolder;
}

.container {
  min-width: 500px;
  max-width: 500px;
  max-height: 520px;
  align-items: center;
  margin: 40px 40px;
  padding: 20px;
  text-align: center;
  border: #222222 solid 1px;
  border-radius: 15px;
}

input, textarea {
  margin: 10px;
  resize: none;
}

textarea {
  height: 150px;
}

.radio_head {
  width: 100px;
  height: 100px;
  margin: 20px;
  border-radius: 5px;
  text-align: center;
  transition: all 500ms ease;
}

#extras {
  background-color: red;
}

#middlas {
  background-color: yellow;
}

#lazys {
  background-color: limegreen;

}

#lazys:hover {
  background-color: green;
  cursor: pointer;
  transform: scale(1.1);


}

#extras:hover {
  background-color: darkred;
  transform: scale(1.1);
  cursor: pointer;
}

#middlas:hover {
  background-color: #aaa606;
  transform: scale(1.1);
  cursor: pointer;
}

span:hover {
  transform: scale(1.1);
}

.btn {
  border: 1px solid;
  border-radius: 5px;
  background-color: white;
  margin: 10px;
  padding: 20px;
}

.btn:hover {
  transform: scale(1.03);
}
</style>
