<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <form @submit.prevent="giveMeACat">
      <div class="form-container row p-3">
        <div class="col-6 d-flex flex-column align-items-end">
          <label for="title">Título: </label>
          <label for="filter">Filtro</label>
          <label for="color">Color</label>
          <label for="size">Tamaño</label>
        </div>
        <div class="col-6 d-flex flex-column align-items-start">
          <input v-model="title" class="mb-1" id="title" type="text">
          <select v-model="filter" class="mb-1" name="filter" id="filter">
            <option disabled value="">Please select one</option>
            <option>blur</option>
            <option>mono</option>
            <option>sepia</option>
            <option>negative</option>
            <option>paint</option>
            <option>pixel</option>
          </select>
          <div class="d-flex">
            <select v-model="color" class="mb-1" name="color" id="color">
              <option disabled value="">Please select one</option>
              <option value="red">rojo</option>
              <option value="blue">azul</option>
              <option value="green">verde</option>
              <option value="white">blanco</option>
              <option value="yellow">amarillo</option>
            </select>
            <span class="circle m-1" :style="{'background-color' : color }"></span>
          </div>
          <input class="mb-1" type="number" v-model.number="size" id="size">
        </div>
      </div>
      <button>Obtener mi gato</button>
    </form>
    <img :src="gif" alt="">
  </div>
</template>

<script>
export default {
  name: 'RandomCat',
  props: {
    msg: String
  },
  data(){
    return {
      title:"",
      color: "",
      filter: "",
      size: 100,
      gif: ""
    }
  },
  methods: {
    giveMeACat(){
      fetch(`https://cataas.com/cat/gif/says/${this.title}?filter=${this.filter}&color=${this.color}&size=${this.size}`)
      .then(data => this.gif = data.url)
      .then(response => this.gif = response )
      }
    }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.form-container{
  background-color: lightcoral;
}
button{
  margin-top: 1em;
  padding: 5px;
}
.circle{
  height: 30px;
  width: 30px;
  border-radius: 50%;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
