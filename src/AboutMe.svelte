<script>
</script>

<style>
  .container {
    max-width: 100vw;
    min-height: 120vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .wrapper {
    display: grid;
    grid-template-columns: 1fr minmax(75%, 1fr);
    background-color: #fff;
    color: #444;
  }

  .about-container {
    display: flex;
    align-items: flex-start;
    justify-content: center;
  }

  .about {
    margin-top: .5rem;
    width: calc(18vmin + 8*(100vw - 400px)/ 400);
  }

  .card-container {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
  }

  .card {
    margin-top: 5rem;
    margin-bottom: 5rem;
    border-left: 4px solid rgb(90, 12, 26);
    padding: 2rem;
    line-height: 2.5rem;
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
  }

  

</style>


<div class="container">
  <div class="wrapper">
    <div class="about-container"><img class="about" src="images/ABOUT.svg" alt="about"></div>
    <div class="card-container">
      <div class="card">
        <div>
          <img class="profile" src="images/profile.jpg" alt="profile image" />
          <p> 
            Wade is a full stack web developer and 2019 Coder Academy boot camp alumnus. Wade completed the 6-month fast track Diploma program at Coder Academy in August 2019 including a four-week internship with Flex Dapps. Coder Academy's program is focussed on job-ready, in-demand web development skills including React, NodeJS, HTML, CSS, Javascript, Express, MongoDB, Ruby and Ruby on Rails. Among his achievements in this program are two full stack web development group projects. The first a marketplace application built using Ruby on Rails deployed with Heroku (Check out the Repo <a href="https://github.com/Wade-Martin/rails_marketplace_app">Here</a>) The second a project partnered with an external business stakeholder built using the MERN stack deployed with NOW.SH and Netlify (Check out the Front End Repo <a href="https://github.com/Wade-Martin/MERN-App-Front-End">Here</a>, and the Back End Repo <a href="https://github.com/timwaldron/MERN-App-Back-End">Here</a>). During his time with Flex Dapps Wade took on a project to rebuild the Web3 Australia Organisation website using Svelte and deployed on Netlify. (Check out the site <a href="https://web3-build.netlify.com/">here</a>)
          </p>
        </div>
        
        <div class="icons">
          <a href="https://github.com/Wade-Martin"><i class="fab fa-github"></i></a>
          <a href="https://codepen.io/wade-martin"><i class="fab fa-codepen"></i></a>
          <a href="https://www.linkedin.com/in/wade-s-martin/"><i class="fab fa-linkedin"></i></a>
          <a href="https://twitter.com/wine_and_Wade"><i class="fab fa-twitter-square"></i></a>
        </div>
      </div>
    </div>
  </div>
</div>


