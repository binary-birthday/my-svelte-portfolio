<script>
  import { scale, slide, fly, fade } from 'svelte/transition';
  import { elasticOut, quintOut } from 'svelte/easing';
  import { onMount } from 'svelte';

  export let elementPos;
  export let scrollPos;
  export let windowHeight;

  let visible = false;

  $: if((scrollPos + (windowHeight *.8)) >= elementPos) {
    console.log('>= init transition in', scrollPos, windowHeight, elementPos)
    visible = true;
  }

   $: if((scrollPos + windowHeight) < elementPos) {
    console.log('< init fade out', scrollPos, windowHeight, elementPos)    
    visible = false;
  }

</script>

<style>
  .main {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .background {
    width: 100%;
    height: 100%;  
    position: absolute;
    z-index: -1;
  }

  .wrapper {
    display: grid;
    height: 100%;
    width: 100%;
    grid-template-columns: minmax(82.5%, 1fr) 1fr;
    color: #444;
  }

  .contact {
    margin-top: 6rem;
    z-index: 2;
    opacity: .5;
    width: calc(10vmin + 8*(100vw - 400px)/ 400);
  }

  .form-container {
    max-width: 60%;
    color: white;
    z-index: 10;
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    margin-top: 3rem;
    padding-left: 3rem;
    width: 70%;
    padding-top: 5rem;
    padding-bottom: 5rem;
    line-height: 2.5rem;
  }

  .dn {
    display: none;
  }

  .form-input {
    color:white;
    font-family: 'Oswald', sans-serif;
    font-weight:500;
    font-size: 18px;
    border-radius: 5px;
    line-height: 22px;
    background-color: transparent;
    border:2px solid rgb(90, 12, 26);
    transition: all 0.3s;
    padding: 13px;
    margin-bottom: 15px;
    width:100%;
    box-sizing: border-box;
    outline:0;
  }

  .form-input:focus { 
    border:2px solid rgba(224, 30, 66, 0.454); 
  }

  textarea {
    height: 150px;
    line-height: 150%;
    resize:vertical;
  }

  [type="submit"] {
    font-family: 'Oswald', sans-serif;
    width: 100%;
    background:rgba(224, 30, 66, 0.454);
    border-radius:5px;
    border:0;
    cursor:pointer;
    color:white;
    font-size:24px;
    padding-top:10px;
    padding-bottom:10px;
    transition: all 0.3s;
    margin-top:-4px;
    font-weight:700;
  }

  [type="submit"]:hover { 
    transform: scale(1.05)
  }

  @media only screen and (max-width: 700px) {
    .form-container {
      max-width: 95%;
      padding-right: 3rem;
      height: 80%;
    }
   
    .background {
      height: 150%;
    }
}
</style>
   

<div class="main" windowHeight={windowHeight} scrollPos={scrollPos} elementPos={elementPos}>
  <svg class="background" viewBox="0 0 1920 1080" preserveAspectRatio="none" fill="none" xmlns="http://www.w3.org/2000/svg">
	  <path d="M1920 1078L1920 0.00305176L0.0020752 0.00622559L0.0020752 402.091V721.995L314.88 643.078L1920 1078Z" fill="black"/>
	  <path d="M1920 1066.7V1079.99L421.496 1079.99L309.761 631.773L1920 1066.7Z" fill="#1D1D1D"/>
	  <path d="M317.44 633.103L709.12 1080H-0.000427246V718.295L317.44 633.103Z" fill="#313131"/>
  </svg>
  <div class="wrapper">
    <div id="form" class="form-container">
    {#if visible }
      <form action="https://formspree.io/wsmartin23@gmail.com" method="POST">      
        <p class="dn">
          <label>Don’t fill this out if you're human: <input name="bot-field" /></label>
        </p>
        <input transition:scale="{{duration: 800, delay: 1000, opacity: 0, start: .8, easing:elasticOut}}" name="name" type="text" class="form-input" placeholder="Name" />   
        <input transition:scale="{{duration: 800, delay: 1050, opacity: 0, start: .8, easing:elasticOut}}" name="email" type="text" class="form-input" placeholder="Email" />
        <textarea transition:scale="{{duration: 800, delay: 1100, opacity: 0, start: .8, easing:elasticOut}}" name="text" class="form-input" placeholder="Your Message here..."></textarea>
        <input transition:scale="{{duration: 800, delay: 1150, opacity: 0, start: .8, easing:elasticOut}}" type="submit" value="SUBMIT"/>
      </form> 
    {/if}
    </div>
    {#if visible }    
    <div class="svg-container">
      <img in:fly="{{delay: 0, duration: 4000, y: -400, opacity: .01, easing: quintOut}}" out:fade="{{delay: 0, duration: 300}}" class="contact" src="images/contact.svg" alt="contact">
    </div>
    {/if}

  </div>
</div>
