<template>
  <div class="hello">
    
    <h2>{{title}}</h2>

    <h2>Skor : {{skor}} </h2>

    <h2 v-if="skor > 60">Anda LULUS</h2>
    <h2 v-else>Anda GAGAL, Ayo coba lagi!</h2>

    <div v-for="(quiz, indexquiz) in questions">

        <b><p>{{indexquiz+1}}. {{quiz.text}}</p></b>

            <div v-for="(choosed) in quiz.responses">

                <input type="radio" @click="checkAnswer(indexquiz,choosed)" :name="indexquiz" :value="choosed">

                <span v-text="choosed"></span>

            </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      title: 'Quiz',
      skor: 0,
      right_answer : [],
      questions: [
          {
            text: "1 + 1 =",
            responses: [
              "1","2","3","4"
            ],
            correct: "2"
          }, 
          {
            text: "Nama Saya adalah...",
            responses: [
              "Annisa","Sidiutami","Sidu",
            ],
            correct: "Annisa"
          },
          {
            text: "Sumpah pemuda lahir pada....",
            responses: [
              "17 Agu","31 Des","28 Nov","28 Okt",
            ],
            correct: "28 Okt"
          },
          {
            text: "Yang dikabarkan habis putus dari Kai EXO adalah",
            responses: [
              "Lisa","Jennie","Rose","Jisoo",
            ],
            correct: "Jennie"
          },
          {
            text: "2^2 = ",
            responses: [
              "4","6","9","2",
            ],
            correct: "4"
          },
          {
            text: "2*2*2*2*2*2*0",
            responses: [
              "0","32","10","72",
            ],
            correct: "0"
          },
          {
            text: "Bahasa Inggris nya Air adalah ...",
            responses: [
              "Air","Wind","Water","Mineral",
            ],
            correct: "Water"
          },
          {
            text: "Perempuan yang hobi berpetualang bernama...",
            responses: [
              "Dora","Sandy","Pearl","Spongebob",
            ],
            correct: "Dora"
          },
          {
            text: "0:0 = ?",
            responses: [
              "0","hmm","tak hingga","tidak ada",
            ],
            correct: "tidak ada"
          },
          {
            text: "Turki merupakan negara yang menghubungkan benua",
            responses: [
              "Asia Afrika","Asia Australia","Asia Eropa","Asia Antartika",
            ],
            correct: "Asia Eropa"
          },
        ]
    }
  },
  methods : {
        checkAnswer(indexquiz,choosed){
            if(this.questions[indexquiz].correct == choosed){
                if(!this.right_answer.includes(indexquiz+1)){
                    this.right_answer.push(indexquiz+1);
                    this.skor +=10;
                }
            }
            else{
                if(this.right_answer.includes(indexquiz+1)){
                    this.right_answer.splice(indexquiz,1);
                    this.skor -=10;
                }
            }
            console.log(this.right_answer);
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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