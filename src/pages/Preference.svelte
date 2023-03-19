<script>
  import { onMount } from "svelte";

  // @ts-nocheck

  import Navbar from "./components/Navbar.svelte";
  import { initVoice } from "./listener/speak";
  import Step1 from "./preference/Step1.svelte";
  import Step2 from "./preference/Step2.svelte";
  import Step3 from "./preference/Step3.svelte";
  import { shutup } from "./store/shutup.store";
  import { suggestions } from "./store/suggestions.store";

  let currentStep = 0;
  let loading = true;
  onMount(() => {
    console.log($suggestions, "$suggestions");
    if (Object.keys($suggestions).length === 0) {
      currentStep = 0;
      $shutup = false;
    } else {
      currentStep = 1;
      $shutup = true;
    }
    loading = false;
    console.log(currentStep, "currentStep");
    initVoice();
  });

  function nextStep() {
    if (currentStep === 2) return;
    currentStep += 1;
  }
  function prevStep() {
    if (currentStep === 0) return;
    currentStep -= 1;
  }
</script>

<section class="flex flex-col min-h-screen h-full ">
  <Navbar />

  <div
    class="flex flex-col justify-center items-center h-full flex-1
  "
  >
    {#if loading}
      <div>Loading...</div>
    {:else if currentStep === 0}
      <Step1 {nextStep} />
    {:else if currentStep === 1}
      <Step2 {nextStep} {prevStep} />
    {:else if currentStep === 2}
      <Step3 {prevStep} />
    {/if}
  </div>
</section>
