<template>
<v-layout align-center justify-center>
<v-btn style="position: fixed;
    right: 0;
    bottom: 0;" small @click.native="references = true">
            references
          </v-btn>
<v-dialog 
  max-width="400px"
  v-model="references"
  scrollable
  style=""

>
<v-card>
        <v-card-title text-align="center"><h2 >References</h2>  </v-card-title>
        <v-divider></v-divider>
        <v-card-text style="height: 300px; overflow-x: hidden;">
        <p><strong>American Cancer Society (ACS). (2018). HPV Facts | HPV Vaccine Facts | How Long is the HPV Vaccine Good For?</strong> <br/>Retrieved from <br/><a target="_blank" href="https://www.cancer.org/cancer/cancer-causes/infectious-	agents/hpv/hpv-vaccine-facts-and-fears.html">https://www.cancer.org/cancer/cancer-causes/infectious-	agents/hpv/hpv-vaccine-facts-and-fears.html</a></p>
        <p><strong>Cancer Council Australia. (2018). Facts about HPV and the vaccine.</strong><br/> Retrieved from <br/>	<a target="_blank" href="http://www.hpvvaccine.org.au/parents/myths-and-facts-about-hpv-and-the-vaccine.aspx">http://www.hpvvaccine.org.au/parents/myths-and-facts-about-hpv-and-the-vaccine.aspx</a></p>
        <p><strong>Centers for Disease Control and Prevention (CDC). (2017). Human Papillomavirus (HPV).</strong><br/> Retrieved from<br/> 	<a target="_blank" href="https://www.cdc.gov/std/hpv/stdfact-hpv.htm">https://www.cdc.gov/std/hpv/stdfact-hpv.htm</a></p>
        <p><strong>Healthy People 2020. (2018). Immunization and Infectious Diseases.</strong><br/> Retrieved from <br/>	<a target="_blank" href="https://www.healthypeople.gov/2020/topics-objectives/topic/immunization-and-	infectious-diseases/objectives">https://www.healthypeople.gov/2020/topics-objectives/topic/immunization-and-	infectious-diseases/objectives</a></p>

<p><strong>Michigan Department of Health and Human Services. (2018a). Ingham County Quarterly Immunization Report Card.</strong><br/> Retrieved from <br/> <a target="_blank" href="https://www.michigan.gov/documents/mdch/Ingham_447454_7.pdf">https://www.michigan.gov/documents/mdch/Ingham_447454_7.pdf</a></p>
<p><strong>National Cancer Institute (NIH). (2018). Human Papillomavirus (HPV) Vaccines.</strong><br/> Retrieved from <br/>
<a target="_blank" href="https://www.cancer.gov/about-cancer/causes-prevention/risk/infectious-agents/hpv-	vaccine-fact-sheet">https://www.cancer.gov/about-cancer/causes-prevention/risk/infectious-agents/hpv-	vaccine-fact-sheet</a></p>

        </v-card-text>
</v-card>
</v-dialog>
<v-dialog 
max-width="400px"
  persistent
      v-model="intro"
    >
       <v-stepper v-model="i1">
    <v-stepper-header>
      <v-stepper-step :complete="i1 > 1" step="1"></v-stepper-step>
      <v-stepper-step :complete="i1 > 2" step="2"></v-stepper-step>
    </v-stepper-header>

    <v-stepper-items>
      <v-stepper-content step="1">
        <v-card
          class="mb-5"
          color=""
          style="text-align:justify; text-align: justify;
    border: 0;
    box-shadow: none;
        display: block;
    margin: 0 auto;"
        >{{currentStat}}</v-card>

        <v-btn
          
          @click="i1 = 2"
        >
          Begin
        </v-btn>

      </v-stepper-content>

      <v-stepper-content step="2">
        <v-card
          class="mb-5"
          color=""
        ></v-card>

          <v-card-text>
            <h3 style="text-align:center; width: 100%;" class="display-1">For demographic purposes:</h3>
            <p>Are you resident in Ingham County, Michigan (East Lansing, Lansing, Holt, etc.)? </p>
            <p>
              <input type="radio" value="yes" v-model="answer">
              <label for="Yes">Yes</label>
              <br>
              <input type="radio" value="no" v-model="answer">
              <label for="No">No</label>
              <br>
              </p>
            </v-card-text>
            <v-btn @click="nextQuestion; beginQuiz(answer)"> Next </v-btn>
        </v-stepper-content>

        

    </v-stepper-items>
  </v-stepper>

</v-dialog >

<v-dialog  
max-width="400px"
  persistent
      v-model="extro"
    >
    <v-stepper v-model="e1">
    <v-stepper-header>
      <v-stepper-step :complete="e1 > 1" step="1"></v-stepper-step>
      <v-stepper-step :complete="e1 > 2" step="2"></v-stepper-step>
      <v-stepper-step :complete="e1 > 3" step="3"></v-stepper-step>
      <v-stepper-step :complete="e1 > 4" step="4"></v-stepper-step>
      <v-stepper-step :complete="e1 > 5" step="5"></v-stepper-step>
      <v-stepper-step :complete="e1 > 6" step="6"></v-stepper-step>
      <v-stepper-step :complete="e1 > 7" step="7"></v-stepper-step>
      <v-stepper-step :complete="e1 > 8" step="8"></v-stepper-step>
    </v-stepper-header>

    <v-stepper-items>
      <v-stepper-content step="1">
        <v-card class="mb-5" color="" style="text-align:justify; text-align: justify; border: 0; box-shadow: none;"
        >This questionnaire is brought to you by a MSU RN-BSN Nursing student.   Please answer the following short questions for research purposes -- again, all answers are anonymous! Thank you!</v-card>

        <v-btn
          
          @click="e1 = 2"
        >
          Sure!
        </v-btn>
        <v-btn
          
          @click="submitQuiz"
        >
          No thanks.
        </v-btn>

      </v-stepper-content>

<v-stepper-content step="2">
        <v-card
          class="mb-5"
          color=""
        >
        
        </v-card>

        <v-card-text>
          <p>Who is affected by HPV?</p>
          <p>
            <select v-model="answer">
              <option selected value="" style="border: 1px solid black;">Please select one</option>
              <option>Males</option>
              <option>Females</option>
              <option>Both</option>
            </select>
            </p>
        </v-card-text>
        <v-btn
          
          @click="e1 = 3; sendExtraAnswers(answer)"
        >
          Next
        </v-btn>

        </v-stepper-content>

      <v-stepper-content step="3">
        <v-card
          class="mb-5"
          color=""
        >
        
        </v-card>

        <v-card-text>
          <p>How is HPV transmitted?</p>
          <p>
            <select v-model="answer">
              <option selected value="" style="border: 1px solid black;">Please select one</option>
              <option>Vaginal sex</option>
              <option>Anal sex</option>
              <option>Oral sex</option>
              <option>All of the above</option>
            </select>
            </p>
        </v-card-text>
        <v-btn
          
          @click="e1 = 4; sendExtraAnswers(answer)"
        >
          Next
        </v-btn>

        </v-stepper-content>

        <v-stepper-content step="4">
        <v-card
          class="mb-5"
          color=""
        >
        
        </v-card>

        <v-card-text>
          <p>Have you already completed your HPV vaccination series?</p>
          <p>
            <select v-model="answer">
              <option selected  value="" style="border: 1px solid black;">Please select one</option>
              <option>Yes</option>
              <option>No</option>
              <option>Currently in the process</option>
              <option>Prefer not to answer.</option>
            </select>
            </p>
        </v-card-text>
        <v-btn
          
          @click="e1 = 5; sendExtraAnswers(answer)"
        >
          Next
        </v-btn>


        </v-stepper-content>

        <v-stepper-content step="5">
        <v-card
          class="mb-5"
          color=""
        >
        
        </v-card>

        <v-card-text>
          <p>Are you interested in starting the HPV vaccination (if eligible Male: 9-21, Female: 9-26) after completing the questionnaire?</p>
          <p>
            <select v-model="answer">
              <option selected value="" style="border: 1px solid black;">Please select one</option>
              <option>Yes</option>
              <option>No</option>
              <option>Already completed/started.</option>
			  <option>Not eligible</option>
              <option>Prefer not to answer.</option>
            </select>
            </p>
        </v-card-text>
        <v-btn
          
          @click="e1 = 6; sendExtraAnswers(answer)"
        >
          Next
        </v-btn>

        </v-stepper-content>

        <v-stepper-content step="6">
        <v-card
          class="mb-5"
          color=""
        >
        
        </v-card>

        <v-card-text>
          <p>If you are a parent, are you interested in starting the HPV vaccination series for your children at the recommended age of 11-12 years after receiving this information?</p>
          <p>
            <select v-model="answer">
              <option selected value="" style="border: 1px solid black;">Please select one</option>
              <option>Yes</option>
              <option>No</option>
              <option>I am not a parent.</option>
              <option>Prefer not to answer.</option>
            </select>
            </p>
        </v-card-text>
        <v-btn
          
          @click="e1 = 7; sendExtraAnswers(answer)"
        >
          Next
        </v-btn>

        </v-stepper-content>

        <v-stepper-content step="7">
        <v-card
          class="mb-5"
          color=""
        >
        
        </v-card>

        <v-card-text>
          <p>Would you consider this questionnaire helpful?</p>
          <p>
            <select v-model="answer">
              <option selected value="" style="border: 1px solid black;">Please select one</option>
              <option>Yes</option>
              <option>No</option>
            </select>
            </p>
        </v-card-text>
        <v-btn
          
          @click="e1 = 8; sendExtraAnswers(answer)"
        >
          Next
        </v-btn>

        </v-stepper-content>

        <v-stepper-content step="8">
        <v-card
          class="mb-5"
          color=""
        >
        
        </v-card>

        <v-card-text>
          <p>Additional Comments(optional)</p>
          <p>
<textarea v-model="answer" placeholder="Enter Comment Here"></textarea>
            </p>
        </v-card-text>
        <v-btn
          
          @click="sendExtraAnswers(answer); submitQuiz()"
        >
          Finish
        </v-btn>

        </v-stepper-content>

        

    </v-stepper-items>
  </v-stepper>
</v-dialog >
<v-dialog  
max-width="400px"
  persistent
      v-model="dialog "
    >
     <v-card v-bind:class="[{ green: isCorrect  }, { red: isIncorrect  } ]">
  <v-card-title>
<h3 style="text-align:center; width: 100%;" class="display-1">{{worTitle}}</h3>
  </v-card-title>
  <v-card-text>
 <p class="body-2" v-html="currentStat" style="text-align:center;" ></p> 
 <v-btn name="Next" v-on:click="nextQuestion">Next</v-btn>
  </v-card-text>
     </v-card>

</v-dialog >

<v-dialog  
max-width="400px"
  persistent
      v-model="thankyou1"
    >
    <v-card>
    <v-card-text>
       <h1> THANK YOU! </h1>
       <p>If you would like to participate in a follow-up study, please provide your email address below.  This follow-up will consist of a 2-question multiple choice survey, sent on 11/19/18 and will be available to answer for 7 days.</p>
       <p>If you aren't submitting an email then you're all done! Thank you for taking the time to respond. I hope you learned something more about HPV.
            </p>
        <p>
<input v-model="email" placeholder="Email address"/>
            </p>
                    <v-btn
          
          @click="sendEmail(email)"
        >
          Send
        </v-btn>
        <v-btn
          
           @click.native="references = true"
        >
          References
        </v-btn>
</v-card-text>
     </v-card>
</v-dialog >
<v-dialog  
max-width="400px"
  persistent
      v-model="thankyou2"
    >
    <v-card>
    <v-card-text>
       <h1> THANK YOU! </h1>
       <p>All done! Thank you for taking the time to respond. I hope you learned something more about HPV.
            </p>
                    <v-btn
          
           @click.native="references = true"
        >
          References
        </v-btn>

</v-card-text>
     </v-card>
</v-dialog >



 <v-flex >
  <v-card >
  <v-card-title>
 <h3 style="text-align:center; width: 100%;" class="display-1">{{cTitle}}</h3>
 </v-card-title>
 <v-card-text>
 <p class="body-2" style="text-align:center;" >{{cQuestion}}</p> 
 
 <ul>
  <li v-for="(answer, index) in cAnswers"
    v-bind:key='index'>
   <v-btn

    name="Answer Option" 
    v-model="answer.answer" 
    label="answer.answer"
    @click="sendAnswer(answer.answer); checkAnswer(answer.answer);">{{answer.answer}}</v-btn>
  </li>
  </ul>
 </v-card-text>
 <v-card-actions justify-content-center>
  <!--<v-btn name="Submit" v-on:click="submitQuiz">SUBMIT</v-btn>-->
 </v-card-actions>
  </v-card>
 </v-flex>
</v-layout>
</template>

<script>
import db from "./firebaseinit";
export default {
  name: "QandA",
  data() {
    return {

      email: '',
      answer: '',
      i1: 0,
      e1: 0,
      worTitle: 'Click Next to Begin',
      currentStat: 'The Human Papillomavirus, commonly known as HPV, is the most common sexually transmitted infection according to the Centers for Disease Control and Prevention (CDC) (2017).  In most cases, HPV will clear on its own, however when HPV does not go away it can cause certain types of cancer (CDC, 2017). Help protect the community of Ingham County and learn more about the vaccination proven to help prevent HPV-associated cancers with this 11 question, 5 minute questionnaire. All answers are recorded anonymously.',
      isCorrect: false,
      isIncorrect: false,
      qc: 0,
      references: false,
      dialog : false,
      intro: true,
      extro: false,
      thankyou1:false,
      thankyou2:false,
      cQuestion:
        '',
      cAnswers: '',
      cTitle: '',
      addAnswer: [],
      questions: [
             
        {
          qTitle: "Question 1",
          qBody: "Now let’s get started. Who is affected by HPV?",
          qAnswers: [
            { answer: "Males Only" },
            { answer: "Females Only" },
            { answer: "Both"}
          ],
          correctAnswer: "Both",
          currentStat: 'According to the Cancer Council of Australia, HPV affects <strong>both</strong> males and females (2018).'
        },
        {
          qTitle: "Question 2",
          qBody: "How many people are affected by HPV during their lifetime?",
          qAnswers: [
            { answer: "9 out of 10" },
            { answer: "3 out of 10" },
            { answer: "7 out of 10" },
            { answer: "5 out of 10" }
          ],
          correctAnswer: "9 out of 10",
          currentStat: '<strong>9 out of 10 people</strong> will have HPV at some point in their lives (Cancer Council of Australia, 2018).  It is the most common STI!'
        },
        {
          qTitle: "Question 3",
          qBody: "How is HPV transmitted?",
          qAnswers: [
            { answer: "Vaginal sex" },
            { answer: "Anal sex" },
            { answer: "Oral sex" },
            { answer: "All of the above" }
          ],
          correctAnswer: "All of the above",
          currentStat: 'HPV can be spread by having <strong>vaginal, anal, or oral sex</strong> with someone who is infected by the virus (CDC, 2018).  An infected person can often have no signs or symptoms. '
        },
        {
          qTitle: "Question 4",
          qBody: "Does HPV cause health problems?",
          qAnswers: [
            { answer: "HPV can cause several types of cancers including cervical, vulva, vagina, penis, anus, and throat (oropharyngeal) cancer." },
            { answer: "HPV has only been linked to cervical cancer." },
            { answer: "HPV can cause genital warts." },
            { answer: "HPV can cause BOTH genital warts and several types of cancer." }
          ],
          correctAnswer: "HPV can cause BOTH genital warts and several types of cancer.",
          currentStat: 'HPV is associated with <strong>several types of cancer along with genital warts</strong> (CDC, 2017).  Luckily,  a vaccination is available to prevent HPV infection and the cancers associated to it.  Protect yourself and others by getting vaccinated.'
        },
        {
          qTitle: "Question 5",
          qBody:
            "If we were to achieve widespread HPV vaccination for the community, cervical cancer rates would decrease by what percentage?",
          qAnswers: [
            { answer: "24%" },
            { answer: "48%" },
            { answer: "72%" },
            { answer: "90%" }
          ],
          correctAnswer: "90%",
          currentStat: 'According to the National Cancer Institute, cervical cancer rates would decrease by <strong>90%</strong> if we were to achieve widespread vaccination for HPV (2018).'
        },
        {
          qTitle: "Question 6",
          qBody: "Is the HPV vaccination safe?",
          qAnswers: [{ answer: "Yes" }, { answer: "No" }],
           correctAnswer: 'Yes',
          currentStat: 'According to the American Cancer Society (ACS), <strong>the HPV vaccine is safe</strong> (2017).  More than 270 million doses of the vaccine have been given worldwide and continues to be proven as safe (ACS, 2017).  <strong>Consult your doctor before receiving the vaccine.</strong> '
        },
        {
          qTitle: "Question 7",
          qBody:
            "It is recommended by the National Cancer Institute that all children aged 11-12 years should get two HPV vaccinations around 6 to 12 months apart (2018).  Up to what age can young adult women and young adult men still receive the vaccine?",
          qAnswers: [
            { answer: "32 years of age" },
            { answer: "18 years of age" },
            { answer: "Men up to age 21 and women up to age 26." },
            { answer: "Men up to age 26 and women up to age 21." }
          ],
          correctAnswer: "Men up to age 21 and women up to age 26.",
          currentStat: 'According to the National Cancer Institute, the HPV vaccination is available to <strong>young adult men through the age of 21 and young adult women through the age of 26</strong> (2018).  It is recommended to receive the vaccine before being sexually active – thus before being exposed to the virus.'
        },
        {
          qTitle: "Question 8",
          qBody:
            "Healthy People provides a 10 year national goal to improve the health of all Americans. Their goal is to have what percentage of adolescents between the age of 13-15 vaccinated for HPV by 2020?",
          qAnswers: [
            { answer: "80%" },
            { answer: "100%" },
            { answer: "40%" },
            { answer: "25%" }
          ],
          correctAnswer: "80%",
          currentStat: 'Answer, Healthy People’s target goal is to achieve <strong>80% compliance of the HPV vaccination series by the year 2020 for BOTH males and females</strong> (2018). '
        },
        {
          qTitle: "Question 9",
          qBody:
            "Knowing the goal of Healthy People 2020, what is the current percentage of female adolescents aged between 13 and 17 years receiving the HPV vaccination in Ingham County? ",
          qAnswers: [
            { answer: "80.2%" },
            { answer: "45.0%" },
            { answer: "25.7%" },
            { answer: "92.4%" }
          ],
          correctAnswer: "45.0%",
          currentStat: 'According to the Michigan Department of Health and Human Services (MDHHS), only <strong>45.0%</strong> of females in this age group has received the HPV vaccination (2018)!'
        },
        {
          qTitle: "Question 10",
          qBody:
            "What about men? What is the current percentage of male adolescents aged between 13 and 17 years receiving the HPV vaccination in Ingham County?  ",
          qAnswers: [
            { answer: "50.0%" },
            { answer: "72.8%" },
            { answer: "39.1%" },
            { answer: "91.1%" }
          ],
          correctAnswer: "39.1%",
          currentStat: 'MDHHS states only <strong>39.1%</strong> of males in this age group have received the HPV vaccination (2018).  Ingham County must double its rates for the HPV vaccination for both males and females to reach the Healthy People goal for the year 2020.'
        },
        {
          qTitle: "",
          qBody:
            "",
          qAnswers: [
            { answer: "" }
          ],
          correctAnswer: "",
          currentStat: ''
        }
      ]
    };
  },
  methods: {
    checkAnswer(answer){
      if(answer !== this.correctAnswer){
        this.isCorrect = false
        this.isIncorrect = true
        this.worTitle = "WRONG"
      }else{this.isCorrect = true
      this.isIncorrect = false
      this.worTitle = "CORRECT!"}
      this.currentStat = this.questions[this.qc].currentStat
    },
    beginQuiz(answer) {
      this.intro = false;
      this.cTitle = this.questions[this.qc].qTitle
      this.cAnswers = this.questions[this.qc].qAnswers
      this.cQuestion = this.questions[this.qc].qBody
      this.addAnswer.push('Do you live in Ingham?: ', answer)
    },
    nextQuestion() {
      this.dialog  = false;
      this.qc++;
      if(this.qc >= 10){
        this.extro = true
      }      
      this.cTitle = this.questions[this.qc].qTitle
      this.cAnswers = this.questions[this.qc].qAnswers
      this.cQuestion = this.questions[this.qc].qBody
    },
    sendAnswer(answer) {     
      this.dialog  = true
      this.correctAnswer = this.questions[this.qc].correctAnswer
      this.isCorrect = true
      this.addAnswer.push(this.cQuestion, answer)
    },
    sendExtraAnswers(answer) {     
      this.addAnswer.push('Extra Info: ' + answer)
      this.answer = ''
    },
      sendEmail(email) {     
      this.email = {Email: this.email}
      db.collection('Responses').add(this.email)
      this.thankyou1 = false
      this.thankyou2 = true
    },
    submitQuiz () {
      this.extro = false
      this.thankyou1 = true
      this.addAnswer = {Quiz: this.addAnswer}
      db.collection('Responses').add(this.addAnswer)
    }
  }
};
</script>
<style scoped>

h1,
h2 {
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
button {
  padding: 5px;
  background: #5a64d6;
  border: none;
  color: white;
}
li div {
    white-space: normal;
    width: 100%;
}
li button {
    white-space: initial;
    width: 100%;
}
.quizWrapper {
  max-width: 400px;
  display: inline-block;
  line-height: 22px;
}
.body-2 {
    font-size: 16px !important;
    font-weight: 500;
    text-align: justify;
}
#app{
  margin-top: 0px !important;
}
.v-overlay:before{
  background-color: red !important;
}
.v-stepper__header{
  display: none;
}
.layout.align-center.justify-center {
    background: #40196b;
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    top: 0;
}

p.body-2 {
    color: white !important;
}

.v-card.theme--light {
    background: #40196b;
    box-shadow: none;
    color: white;
    max-width: 400px;
    display: inline-block;
}

button.v-btn.v-btn--active.theme--light {
    background-color: #FF970D !important;
    color: black;
    margin: 5px;
    padding: 10px;
}
.v-btn__content {
    white-space: normal;
}
button.v-btn.theme--light {
    background-color: #FF970D !important;
    height: auto;
}
.v-stepper.theme--light {
    background: #40196b;

}
.v-card__text {
    color: white !important;
}
.v-btn /deep/ div{
  white-space: normal !important;
}
select{
  border: 1px solid white;
    text-align: center;
    padding: 5px;    
}
textarea, input {
    border: 1px solid white;
    padding: 2px;
}
option{
  color: black;
}
</style>
