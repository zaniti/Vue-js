<template>
  <div class="container">
   <div class="cv">
        <div class="container card">
        <h1 id="br">infos personnelles</h1>
        <h2> description : {{ description }}</h2>
        <h2> name : {{ name }}</h2>
        <h2>email : {{ email }}</h2>
        <h2>adress :{{ adress }}</h2>
        <h2>phone : {{ phone }}</h2>
        <h2>github : {{ github }}</h2>
     
  </div>
    <div class="container card">
      <h1 id="br">infos professionnelles</h1>
      <div v-for="(experience, index) in experiences" :key="index">
        <div class="contents">
          <h4> COMPANY : {{ experience.COMPANY }}</h4>
          <h5>
           POST: {{ experience.POST }} |
            <span> FROM: {{ experience.FROM }} - TO :{{ experience.TO }} </span>
          </h5>
          <p>POST_DESC :{{experience.POST_DESC }}</p>
        </div>
        <br />
      </div>
       </div>

    <div class="container card">
      <h1 id="br">EDUCATION</h1>
      <div v-for="(education, index) in educations" :key="index">
        <div class="contents">
          <h4>UNIVERSITY :{{ education.UNIVERSITY }}</h4>
          <h5>BRANCH: {{ education.BRANCH }} |
            <span>FROM :{{  education.FROM }} - TO:{{ education.TO }}</span>
          </h5>
        </div>
        <br />
      </div>
            </div>

      

    <div class="container card">
      <h1>ABOUT ME</h1>
      <p class="aboutMe">{{ about }}</p>
    
            </div>

    
        </div>

  </div>
  
</template>
<script>
  import jsPDF from 'jspdf'
  export default {
    name: "About",
    data() {
      return {
        name: this.$store.state.name,
        description: this.$store.state.desc,

        email: this.$store.state.email,
        phone: this.$store.state.phone,
        adress: this.$store.state.adress,
        github: this.$store.state.github,

        experiences: this.$store.state.experinceList[0],

        educations: this.$store.state.educationList[0],

        // skills: this.$store.state.skillsList[0],

        about: this.$store.state.about,
      };
    },
    methods: {
      downloadPDF: function () {
        var pdf = new jsPDF(); 
        pdf.html(window.document.getElementsByClassName("cv")[0], {
          callback: function (pdf) {
            pdf.save();
          },
          x: 10,
          y: 10
        });
      }
    }
  }
</script>
  <style>
  .h1{
    color:black;
  }
  
  h2{
    color: gray;
    margin-left:-20%;
  }
  .card{
    padding-bottom: 30px;
    margin-bottom: 20px;
}
.btn{
  width:100%;
}
  

  </style>
