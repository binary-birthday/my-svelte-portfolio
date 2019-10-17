<script>
  import { fly, fade } from 'svelte/transition';
  import { quintOut, sineIn } from 'svelte/easing';
  import { afterUpdate } from 'svelte';

  export let scrollPos;
  export let loaded = false;

</script>

<style>
  .container {
    width: 100%;
    min-height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .wrapper {
    display: grid;
    height: 100%;
    width: 100%;
    grid-template-columns: 1fr minmax(82.5%, 1fr);
    background-color: #fff;
  }

  .about-container {
    display: flex;
    align-items: flex-start;
    justify-content: center;
  }

  .about {
    margin-top: 4rem;
    z-index: 2;
    width: calc(12vmin + 8*(100vw - 400px)/ 400);
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
      margin-right: .75rem;
      margin-bottom: .5rem;
    }
    .card {
      padding-left: 1rem;
      line-height: 2rem;
      width: 90%;
    }
    .about {
      margin-top: 2rem;
    }
}

</style>


<div class="container" loaded={loaded}>
  
  <div class="wrapper">
    {#if scrollPos > 100} 
    <div class="about-container">
      <img in:fly="{{delay: 0, duration: 4000, y: -400, opacity: .01, easing: quintOut}}" out:fade="{{delay: 250, duration: 300}}" class="about" src="images/ABOUT.svg" alt="about">
    </div>
    <div class="card-container">
      <div transition:fly="{{delay: 100, duration: 3000, y: 200, opacity: .75, easing: quintOut}}" class="card">
        <div>
          <img class="profile" src="images/profile.jpg" alt="profile image" />
          <p> 
            Who is Wade you ask? Well, among other things I'm a wine lover, hiker, sports tragic and fantasy novel enthusiast. In February 2019 I embarked on an exciting journey into the world of web development undertaking a 6-month fast track boot-camp-style diploma program @CoderAcademy in Melbourne and what a fun ride it was! Now out the other side after (successful!) completion of my Coder Academy journey I'm keeping my skills sharp building new things (this portfolio for one) and learning new skills (like SVG and other front-endy type things) and am bursting at the seems to get my new career as a web developer off and running! Having made the move north from Melbourne to Sydney in October 2019 I am actively seeking my first professional web development role here in the Harbour city.
            
            <!-- Her are some links to a few of my Coder Academy projects:
             using Ruby on Rails deployed with Heroku (Check out the Repo <a href="https://github.com/Wade-Martin/rails_marketplace_app" target="_blank">Here</a>). The second a project partnered with an external business stakeholder built using the MERN stack deployed with NOW.SH and Netlify (Check out the Front End Repo <a href="https://github.com/Wade-Martin/MERN-App-Front-End" target="_blank">Here</a>, and the Back End Repo <a href="https://github.com/Wade-Martin/MERN-App-Back-End" target="_blank">Here</a>). During his time with Flex Dapps Wade took on a project to rebuild the Web3 Australia Organisation website using Svelte and deployed on Netlify. (Check out the site <a href="https://web3-build.netlify.com/" target="_blank">here</a>) -->
          </p>
        </div>
        <div class="icons">
          <a href="https://github.com/Wade-Martin" target="_blank">   <i class="fab fa-github">    </i></a>
          <a href="https://codepen.io/wade-martin" target="_blank"><i class="fab fa-codepen">   </i></a>
          <a href="https://www.linkedin.com/in/wade-s-martin/" target="_blank"><i class="fab fa-linkedin">    </i></a>
          <a href="https://twitter.com/wine_and_Wade" target="_blank">    <i class="fab fa-twitter-square"></i></a>
        </div>
      </div>
    </div>
    {/if}
  </div>
</div>


