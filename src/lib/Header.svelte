<script lang="ts">
  import Circles from "../images/pattern-circles.svg";
</script>

<main class="z-10 relative">
  <div
    class="bg-[#F1F5FE] relative w-full z-10 px-[32px] pb-[198px] pt-[57px] flex flex-col items-center text-center rounded-bl-[191px]"
  >
    <div class="relative w-[312px] md:w-[393px]">
      <img
        src={Circles}
        alt="Circles"
        class="w-[146px] items-center justify-center mx-auto"
      />
      <div class="absolute top-9">
        <div class="mx-auto items-center flex flex-col gap-3 justify-center">
          <h1 class="text-[#293356] text-xl md:text-[28px] font-extrabold">
            Simple, traffic-based pricing
          </h1>
          <p
            class="text-[#848EAD] text-[13px] md:text-[15px] font-semibold leading-6"
          >
            Sign-up for our 30-day trial. No credit card required.
          </p>
        </div>
      </div>
    </div>
  </div>
</main>
