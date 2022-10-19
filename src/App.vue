<template>
  <div id="app">
    <h3>Eample</h3>
    <hr>
    <form @submit.prevent="addSubject" class="inputForm">
      <label for="item">Enter new  subject:</label>
      <input type="text" v-model="newSubject">
      <button>Add subject</button>
    </form>
    <hr>
    <ul>
      <li v-for="(item,index) in allSubjects">
        {{ item.content }}
        <button  @click="removeSubject(index)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
import {ref} from "vue";

export default {
  setup() {
    const newSubject = ref("Mittwoch");
    const allSubjects = ref([])

    function addSubject() {
      allSubjects.value.push({
        content: newSubject.value,
      })
      newSubject.value = "";
      console.log(allSubjects.value);
    }

    function removeSubject(index){
      console.log("remove " + index);
      allSubjects.value.splice(index,1);
    }

    return {
      newSubject,
      addSubject,
      allSubjects,
      removeSubject
    }
  }
  
}
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

h3 {
  margin-bottom: 20p;
}

.inputForm {
  display:flex;
  justify-content: space-between;
}

ul li button {
  margin-left: 35px;
}
</style>
