<script>
  import { scale, fade, slide } from 'svelte/transition';
  import { onMount } from 'svelte';
  import { elasticOut, quintOut } from 'svelte/easing';

  let element 
  let getRect
  let position

  export let y;

  onMount(() => {
    element = document.getElementById("background");
    getRect = element.getBoundingClientRect();
    position = getRect.top;
  })
</script>

<style>
  .background {
    width: 100vw;
    height: 100%;  
    position: absolute;
    z-index: -1;
  }

  .main {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
  }
  
  .left {
    height: 100%;
    width: 50%;
  }

  .form-container {
    max-width: 60%;
    height: 90%;
    color: white;
    z-index: 10;
    display: flex;
    flex-direction: column;
    align-items: flex-end;
    margin-top: 2rem;
    padding: 1rem 6rem 1rem 0;
  }

  h1 {
    align-self: flex-start;
    padding: 1rem 1rem 1rem 0;
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

    }
    .background {
      height: 150%;
    }
}
</style>

<svg class="background" id="background" viewBox="0 0 1920 1080" preserveAspectRatio="none" fill="none" xmlns="http://www.w3.org/2000/svg">
	<path d="M1920 1078L1920 0.00305176L0.0020752 0.00622559L0.0020752 402.091V721.995L314.88 643.078L1920 1078Z" fill="black"/>
	<path d="M1920 1066.7V1079.99L421.496 1079.99L309.761 631.773L1920 1066.7Z" fill="#1D1D1D"/>
	<path d="M317.44 633.103L709.12 1080H-0.000427246V718.295L317.44 633.103Z" fill="#313131"/>
</svg>
<div class="main">
  <div class="left"></div>
  <div class="form-container">
    {#if y > (position - 10)}
    <h1 in:slide="{{delay: 100, duration: 1000, easing: quintOut }}" out:fade="{{delay: 0, duration: 1000}}" >Get In Touch</h1>
    <form action="https://formspree.io/wsmartin23@gmail.com" method="POST">      
      <p class="dn">
        <label>Don’t fill this out if you're human: <input name="bot-field" /></label>
      </p>
      <input in:scale="{{duration: 1000, delay: 500, opacity: 0, start: .75, easing:elasticOut}}" out:fade="{{delay: 0, duration: 1000}}" name="name" type="text" class="form-input" placeholder="Name" />   
      <input in:scale="{{duration: 1000, delay: 550, opacity: 0, start: .75, easing:elasticOut}}" out:fade="{{delay: 0, duration: 1000}}" name="email" type="text" class="form-input" placeholder="Email" />
      <textarea in:scale="{{duration: 1000, delay: 600, opacity: 0, start: .75, easing:elasticOut}}" out:fade="{{delay: 0, duration: 1000}}" name="text" class="form-input" placeholder="Your Message here..."></textarea>
      <input in:scale="{{duration: 1000, delay: 650, opacity: 0, start: .75, easing:elasticOut}}" out:fade="{{delay: 0, duration: 1000}}" type="submit" value="SUBMIT"/>
    </form> 
    {/if}
  </div>
</div>
