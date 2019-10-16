<script>
  import { fly } from 'svelte/transition';
  import { quintOut, sineIn } from 'svelte/easing';
  import { onMount } from 'svelte';
  
  let element 
  let getRect
  let position

  export let y;

  onMount(() => {
    element = document.getElementById("container");
    getRect = element.getBoundingClientRect();
    position = getRect.top - 50;
    consolelog(position)
  })
</script>

<style>
  .container {
    width: 100vw;
    min-height: 120%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .wrapper {
    display: grid;
    grid-template-columns: 1fr minmax(82.5%, 1fr);
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
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .card {
    width: 70%;
    padding-top: 5rem;
    padding-bottom: 5rem;
    line-height: 2.5rem;
  }

  .profile {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    float: left;
    object-fit: cover;
    object-position: center;
    margin-right: 1.2rem;
    margin-bottom: 1rem;
    opacity: .7;
  }

  p {
    font-size: 1.25rem;
    font: 300;
    font-family: 'Cormorant', serif;
    padding-right: 2rem;
  }

  .icons {
    width: 90%;
    height: 4rem;
    display: flex;
    align-self: center;
    align-items: center;
    justify-content: space-around;
  }

  i {
    font-size: 1.5rem;
  }

  @media only screen and (max-width: 700px) {
    .profile {
      width: 75px;
      height: 75px;
      margin-right: 1rem;
      margin-bottom: .75rem;
    }
    .card {
      padding-left: 1rem;
      line-height: 2rem;
      width: 90%;
    }
    .profile {
      margin-right: .75rem;
      margin-bottom: .5rem;
    }
}

</style>


<div id="container"  class="container">
  <div class="wrapper">
    <div class="about-container">
      {#if y > position }
        <img in:fly="{{delay: 0, duration: 2000, y: -300, opacity: .01, easing: quintOut}}" class="about" src="images/ABOUT.svg" alt="about">
      {/if}
    </div>
    <div class="card-container">
      {#if y > position }
      <div transition:fly="{{delay: 100, duration: 3000, y: 200, opacity: .75, easing: quintOut}}" class="card">
        <div>
          <img class="profile" src="images/profile.jpg" alt="profile image" />
          <p> 
            Wade is a full stack web developer and 2019 Coder Academy boot camp alumnus. Wade completed the 6-month fast track Diploma program at Coder Academy in August 2019 including a four-week internship with Flex Dapps. Coder Academy's program is focussed on job-ready, in-demand web development skills including Javascript, React, NodeJS, Express, Ruby and Ruby on Rails. Among his achievements in this program are two full stack web development group projects. The first a marketplace application built using Ruby on Rails deployed with Heroku (Check out the Repo <a href="https://github.com/Wade-Martin/rails_marketplace_app" target="_blank">Here</a>). The second a project partnered with an external business stakeholder built using the MERN stack deployed with NOW.SH and Netlify (Check out the Front End Repo <a href="https://github.com/Wade-Martin/MERN-App-Front-End" target="_blank">Here</a>, and the Back End Repo <a href="https://github.com/Wade-Martin/MERN-App-Back-End" target="_blank">Here</a>). During his time with Flex Dapps Wade took on a project to rebuild the Web3 Australia Organisation website using Svelte and deployed on Netlify. (Check out the site <a href="https://web3-build.netlify.com/" target="_blank">here</a>)
          </p>
        </div>
        <div class="icons">
          <a href="https://github.com/Wade-Martin" target="_blank">   <i class="fab fa-github">    </i></a>
          <a href="https://codepen.io/wade-martin" target="_blank"><i class="fab fa-codepen">   </i></a>
          <a href="https://www.linkedin.com/in/wade-s-martin/" target="_blank"><i class="fab fa-linkedin">    </i></a>
          <a href="https://twitter.com/wine_and_Wade" target="_blank">    <i class="fab fa-twitter-square"></i></a>
        </div>
      </div>
      {/if}
    </div>
  </div>
</div>


