<template>
  <div id="mount">
    <div id="quote-machine">
      <h2 id="quote">'' {{ quote }} ''</h2>
      <p id="author">-{{ author }}</p>
      <button id="getQuote" @click="getQuote">New Quote</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  data() {
    return {
      quote:'To generate a quote, click the button bellow.',
      author:'Xant3r'
    } 
  },
  methods:{
    async getQuote() {
      const fromServe = await axios.get('https://api.api-ninjas.com/v1/quotes',{headers:{'X-Api-Key':'wxRunU6H9yhJkzZVRuV20g==xYPyArZMoN3o6r8Q'}});
      //console.log(axios.get('https://api.api-ninjas.com/v1/quotes',{headers:{'X-Api-Key':'wxRunU6H9yhJkzZVRuV20g==xYPyArZMoN3o6r8Q'}}))
      this.quote = fromServe.data[0].quote;
      this.author = fromServe.data[0].author;
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: 'Raleway', sans-serif;
}
#author {
  text-align:end;
  color:#ffff;
  margin-bottom: 3vh;
}
#quote {
  color:#ffff;
  margin-bottom: 3vh;
  text-align: center;
}
#mount {
  width: 100vw;
  height: 100vh;
  display:flex;
  justify-content: center;
  align-items: center;
}
#quote-machine {
  width: 50vw;
  height:fit-content;
  align-self: center;
  background-color:black;
  padding:30px;
  display:flex;
  flex-direction: column;
  border-radius:5px;
}
#getQuote {
  align-self:flex-end;
  background-color: #ffff;
  color: #000;
  border:none;
  padding:1vw;
  border-radius: 5px;
}
@media(max-width:1000px) {
  #quote {
  color:#ffff;
  margin-bottom: 3vh;
  font-size:1.17em;
  }
  #quote-machine {
  width:50vw;
  height:fit-content;
  align-self: center;
  background-color:black;
  padding:30px;
  display:flex;
  flex-direction: column;
  border-radius:5px;
  }
}
@media(max-width:500px) {
  #quote {
  color:#ffff;
  margin-bottom: 3vh;
  font-size:1em;  
  }
  #quote-machine {
  width:fit-content;
  height:fit-content;
  align-self: center;
  background-color:black;
  padding:30px;
  display:flex;
  flex-direction: column;
  border-radius:5px;
  }
}
</style>