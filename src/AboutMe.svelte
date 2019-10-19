<script>
  import { fly, fade } from 'svelte/transition';
  import { quintOut, sineIn } from 'svelte/easing';
  import { afterUpdate } from 'svelte';

  export let scrollPos;
  export let height;

</script>

<style>
  .container {
    width: 100%;
    min-height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-basis: content;
  }

  .wrapper {
    display: grid;
    width: 70%;
    grid-gap: .5rem;
    margin-top: 5rem;
    margin-bottom: 5rem;
    grid-template-columns: 1fr minmax(85%, 1fr);
  }

  .about-container {
    display: flex;
    flex-basis: content;
    justify-content: center;
    align-items: flex-start;
  }

  .about {
    z-index: 2;
    width: calc(12vmin + 8*(100vw - 400px)/ 400);
    opacity: .5;
  }

  .card-container { 
    height: 100%;
    width: 100%;
    display: flex;
    flex-basis: content;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    border: 2px solid var(--brandBlue);
    border-radius: 5px;
  }

  .card {
    width: 95%;
    height: 95%;
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
    transform: translateX(1%)
  }

  p {
    font-size: 1.5rem;
    font-weight: 600;
    font-family: 'Cormorant', serif;
    color: white;
  }

  .icons {
    width: 90%;
    height: 4rem;
    display: flex;
    align-self: center;
    align-items: center;
    justify-content: space-around;
    opacity: .4;
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
      line-height: 2rem;
      width: 100%;
    }
    .about {
      margin-top: 2rem;
    }
    .wrapper {
      width: 100%
    }
    p {
      font-size: 1.2rem;
    }
}

</style>


<div class="container" bind:offsetHeight={height} >
  <div class="wrapper">
    {#if scrollPos > 100} 
    <div class="about-container">
      <img in:fly="{{delay: 800, duration: 3000, y: -400, opacity: .01, easing: quintOut}}" out:fade="{{delay: 250, duration: 2000}}" class="about" src="images/ABOUT.svg" alt="about">
    </div>
    <div class="card-container" in:fly="{{delay: 800, duration: 3000, y: 150, opacity: 0, easing: quintOut}}" out:fade="{{delay: 250, duration: 2000}}">
      <div class="card">
        <img class="profile" src="images/profile.jpg" alt="profile image" />
        <p> 
          "Who is Wade?" I hear you ask. Well, among other things I'm a wine lover, hiker, sports tragic and fantasy novel enthusiast. In February 2019 I embarked on an exciting journey into the world of web development undertaking the boot-camp-style 6-month fast track diploma program @CoderAcademy, and what a fun ride it was! Now out the other side after (successfully!) completing my Coder Academy adventure I'm keeping my skills sharp building new things (this portfolio for one) and learning new skills (like SVG and other front-endy type things) and I could not be more excited about my future in web development! Having made the move north from Melbourne to Sydney in October 2019 I am actively seeking my first professional web development role here in the Harbour city.
        </p>
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


