<template>
  <form @submit.prevent="registerAnswer">
    <input v-model="inpVal" placeholder="todo">
    <button type="submit">Submit</button>
  </form>
  <div>
    <h3>Submitted choice:</h3>
    <li id="pAnswer" v-for="(item, index) in inpValSubmitted" :key="index">{{ item }}</li>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inpVal: '',
      inpValSubmitted: JSON.parse(localStorage.getItem('submittedAnswers')) || []
    }
  },
  methods: {
    registerAnswer() {
      if(this.inpVal.trim()) {
        this.inpValSubmitted.push(this.inpVal);
        localStorage.setItem('submittedAnswers', JSON.stringify(this.inpValSubmitted));
        this.inpVal = '';
      }
    }
  }
}
</script>


<style scoped>
  div {
    border: dashed black 1px;
    border-radius: 10px;
    padding: 0 20px 20px 20px;
    margin-top: 20px;
    display: inline-block;
  }
  button {
    margin: 10px;
  }
  label {
    display: block;
    width: 80px;
    padding: 5px;
  }
  label:hover {
    cursor: pointer;
    background-color: rgb(211, 244, 211);
    border-radius: 5px;
  }
  #pAnswer {
    background-color: #111111;
    padding: 5px;
  }
</style>
