<div class="bg-slate-900 flex w-full justify-center h-screen">

  <div class="rounded-lg h-72 w-[430px] md:w-[440px] bg-slate-600  text-center self-center">
    <h4 class="font mt-4 text-green-400 text-xs tracking-wider font-bold">ADVICE #{adviceId}</h4>
    {#if visible}
    <h4 transition:fade class="font mt-20 text-xl md:text-2xl text-white">"{getAdvice}"</h4>
    {/if}
    <img class="mt-10" src="./src/assets/pattern-divider-desktop.svg" >
    <button on:click={renewQuote} class="mt-7 mx-auto px-4 py-4 rounded-full bg-emerald-200">
      <img src="./src/assets/icon-dice.svg">
    </button>
  </div>
</div>
<script>
  import axios from "axios";
  import { onMount } from 'svelte';
  import { fade } from 'svelte/transition';
  
  let visible = true;

  const baseUrl = "https://api.adviceslip.com/advice";
  let Advices = [];
  let getAdvice = ""
  let adviceId = ""


  const newAdvice = () =>{
    axios.get(baseUrl)
        .then((res) => {Advices = res.data; 
          console.log("type>>",typeof(Advices.slip));
          getAdvice = Advices.slip.advice;
          adviceId = Advices.slip.id;
           console.log("getadd>>",getAdvice);
        })
        .catch((err) =>{
          console.log(err.message);
        })
  }

  onMount(() =>{
    newAdvice();
  })

  const renewQuote = (e) =>{
    e.preventDefault();
    window.location.reload();
  }
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');
.font{
  font-family: 'Poppins', sans-serif;
}
</style>