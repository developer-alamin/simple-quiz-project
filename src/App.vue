<script setup>
  import { ref,reactive } from 'vue';
  const conutries = reactive([
      {name:"Bangladesh",capital:"Dhaka"},
      {name:"Afghanistan",capital:"Kabul"},
      {name:"Australia",capital:"Canberra"},
      {name:"Korea",capital:"Seoul"},
      {name:"Malaysia",capital:"Kuala Lumpur"},
      {name:"Pakistan",capital:"Islamabad"}, 
  ]);
  const capitals = ["Dhaka","Kabul","Canberra","Seoul","Kuala Lumpur","Islamabad"];
  function getScore(){
    let score = 0;
    conutries.forEach((conutry) =>{
      if (conutry.answer === conutry.capital) {
        score++;
      }
    });
    return score;
  } 
  function capitalSort(){
    return capitals.sort(()=>Math.random() - 0.5);
  }


</script>
<template>
  <div class="card">
    <h4 class="text-center">Simple Quize App</h4>
    <hr>
    <div class="answerList">
      <h6>{{ conutries }}</h6>
    </div>
    <div class="scoreDiv">
      <h5>Your Score: {{ getScore() }}</h5>
    </div>  
    <div class="card-body">
        <div class="card mt-2 card-body" v-for="(conutry,index) in conutries" :key="index">
          <div class="questionList">
            <h5>What's Is The Capital Of {{ conutry.name }} ?</h5>
          </div> 
           <div class="row">
             <div class="questionDiv col-2" v-for="(capital,i) in capitalSort()" :key="i">
            <input type="radio" :name="conutry.name" :value="capital" v-model="conutry.answer">
            <label>{{ capital }}</label>
          </div>
           </div>
        </div>
    </div>
  </div>
</template>

<style scoped>
  label{
    margin-left:5px;
  }

</style>
