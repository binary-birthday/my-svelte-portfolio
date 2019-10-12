<script>
</script>

<style>
  .about-container {
    width: 100vw;
    display: flex;
    flex-wrap: wrap;
  }

  .card {
    margin: 3rem;
    max-width: 30rem;
    border-left: 4px solid rgb(90, 12, 26);
    padding: 2rem;
    background-color: rgba(0, 0, 0, .9);
    color: white;
  }

  .profile {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    float: left;
    object-fit: cover;
    object-position: center;
    margin-right: 2rem;
    margin-bottom: 1rem;
    opacity: .7;
  }

  p {
    font-size: 1.5rem;
    font: 300;
    font-family: 'Cormorant', serif;
  }

  .icons {
    width: 80%;
    height: 4rem;
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    padding-left: 2rem;
  }

  i {
    font-size: 1.5rem;
    color: white;
  }


</style>

<div class="about-container">
  <div class="card">
    <div>
      <img class="profile" src="images/profile.jpg" alt="profile image" />
      <p> 
        Wade is a full stack web developer and 2019 Coder Academy alumnus. Wade begun the 6 month boot camp style, fast track Diploma program at Coder Academy in February 2019. Th program is focussed on job ready, in demand web development skills. Among his acheivements in this program Wade completed two full stack web development group projects, the first a marketplace application built using Ruby on Rails deployed with Heroku (<a href="https://github.com/Wade-Martin/rails_marketplace_app">GitHub Repo</a>) and the second a project partnered with an external business stakeholder built with MERN stack application delpoyed with NOW.SH and Netlify (<a href="https://github.com/Wade-Martin/MERN-App-Front-End">Front End GitHub Repo</a>, <a href="https://github.com/timwaldron/MERN-App-Back-End">Back End GitHub Repo</a>).
      </p>
    </div>
    <div class="icons">
      <a href="https://github.com/Wade-Martin"><i class="fab fa-github"></i></a>
      <a href="https://codepen.io/wade-martin"><i class="fab fa-codepen"></i></a>
      <a href="https://www.linkedin.com/in/wade-s-martin/"><i class="fab fa-linkedin"></i></a>
      <a href="https://twitter.com/wine_and_Wade"><i class="fab fa-twitter-square"></i></a>
    </div>
  </div>
  <div class="card"></div>
</div>
