<template>
  <div id="app">
    <h1>{{title}}</h1>
    <div class="form">
      <div class="form-group">
        <label>Title</label>
        <input class="form-control" type="text" v-model="note.title" />
      </div>
      <div class="form-group">
        <label>Text</label>
        <textarea class="form-control" v-model="note.text"></textarea>
      </div>
      <button class="btn btn-primary" @click="addNote">Enviar</button>
    </div>
    <div class="col-sm-12">
      <div class="col-sm-4 nota" v-for="(note, index) in notes">
        <div class="card">
          <div class="card-block">
            <div class="card-title">{{note.title}}</div>
            <div class="card-subtitle mb-2 text-muted">{{note.date}}</div>
            <div class="card-text">{{note.text}}</div>
          </div>
          <button class='close' @click='deleteNote(index)'> &times;</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      title: "Gestor de notas",
      note: {
        title: "",
        text: ""
      },
      notes: [
        {
          title: "Ir al cine",
          text: "Mirar las peliculas de estrenos y elegir una",
          date: new Date(Date.now()).toLocaleString()
        }
      ]
    };
  },
  methods: {
    addNote: function() {
      let { text, title } = this.note;
      this.notes.push({
        text,
        title,
        date: new Date(Date.now()).toLocaleString()
      });
    },
    deleteNote: function(index){
      this.notes.splice(index, 1)
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: Arial, Helvetica, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin: 20px;
}
.form {
  text-align: left;
}
.card {
  text-align: left;
  border: 1px solid #2c3e50;
  border-radius: 4px;
  padding-left: 8px;
  padding-right: 8px;
}
.nota {
  padding: 5px;
}
</style>
