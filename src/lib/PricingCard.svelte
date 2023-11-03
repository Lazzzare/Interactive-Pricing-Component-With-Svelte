<script lang="ts">
  import Check from "./../images/icon-check.svg";

  let fill = false;
  // PROPS
  export let rangeValue: number;
  export let initialRange: number;
  export let initialpageViews: number;
  export let monthly: boolean;

  const handleClick = () => {
    fill = !fill;
    monthly = !monthly;

    const scaleFactor = monthly ? 0.5 : 2;

    rangeValue *= scaleFactor;
    initialRange *= scaleFactor;
    initialpageViews *= scaleFactor;
  };

  let previousValue: number = 0;

  const updateValues = () => {
    const inputValue = parseFloat(
      (document.querySelector('input[type="range"]') as HTMLInputElement).value
    );
    const valueChange = inputValue - previousValue;
    rangeValue = inputValue;

    if (monthly) {
      initialRange += valueChange * 6;
      initialpageViews += valueChange * 10;
    } else {
      initialRange += valueChange * 12;
      initialpageViews += valueChange * 20;
    }
    previousValue = inputValue;
  };
</script>

<main
  class="box bg-white z-50 absolute top-[230px] mx-auto right-0 left-0 px-6 w-[327px] md:w-[540px]"
>
  <!-- Range input and price -->
  <div class="flex flex-col gap-6 items-center pt-8 pb-8 pr-3 pl-6 z-50">
    <h2
      class="text-[#848EAD] text-xs md:text-2xl font-extrabold tracking-[1.7px] uppercase"
    >
      {initialpageViews}K PAGEVIEWS
    </h2>
    <input
      type="range"
      class="myrange w-full"
      min={0}
      max={5}
      bind:value={rangeValue}
      on:input={updateValues}
    />
    <span
      class={`text-[#293356] text-[32px] font-extrabold tracking-[-0.8px] ${
        monthly ? "after:content-['/month']" : "after:content-['/year']"
      } after:text-[#32343b] after:pl-2 after:text-sm`}
    >
      ${initialRange}.00
    </span>
  </div>
  <div class="pb-10 items-center text-center mx-auto flex justify-center">
    <!-- Monthly/Yearly -->
    <div
      class="flex flex-row gap-3 items-center text-[#848EAD] text-xs md:text-lg"
    >
      <h3>Monthly Billing</h3>
      <button on:click={handleClick}>
        <!-- ON/OFF -->
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="44"
          height="22"
          viewBox="0 0 44 22"
          fill="none"
        >
          <rect
            x="0.5"
            width="43"
            height="22"
            rx="11"
            fill={fill ? "#7AEADF" : "#CFD8EF"}
          />
          <circle
            cx={fill ? "30" : "11.5"}
            cy="11"
            r="7"
            fill={fill ? "white" : "white"}
          />
        </svg>
      </button>
      <h3
        class="after:content-['-25%'] after:bg-[#FEEDE8] after:rounded-lg md:after:text-[12px] after:px-[7px] after:py-[2px] after:text-[#FF8D68] after:font-extrabold after:text-[10px] after:ml-1"
      >
        Yearly Billing
      </h3>
    </div>
  </div>
  <!-- HR -->
  <hr class="w-full h-[1px] bg-[#ECF0FB]" />
  <div class="flex flex-col gap-4 mx-auto items-center justify-center py-8">
    <div class="flex flex-row items-center gap-3">
      <img src={Check} class="w-[10px] h-[10px]" alt="Check" />
      <h4>Unlimited websites</h4>
    </div>
    <div class="flex flex-row items-center gap-3">
      <img src={Check} class="w-[10px] h-[10px]" alt="Check" />
      <h4>100% data ownership</h4>
    </div>
    <div class="flex flex-row items-center gap-3">
      <img src={Check} class="w-[10px] h-[10px]" alt="Check" />
      <h4>Email reports</h4>
    </div>
  </div>
</main>
