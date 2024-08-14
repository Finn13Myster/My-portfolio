<script>
    import "../app.css";
    import Footer from "../components/Footer.svelte";
    import Header from "../components/Header.svelte";

    let y;
    let innerHeight = 0
    let innerWidth = 0

    function goTop() {
      document.body.scrollIntoView()
    }
  </script>
  
  <div class="relative flex flex-col max-w-[1400px] mx-auto w-full text-sm 
  sm:text-base min-h-screen">
      <div class={"fixed bottom-0 w-full duration-200 flex p-10 z-[10] " + (
        y > 0 ? ' opacity-full pointer-events-auto ':' pointer-events-none opacity-0 '
      )}>
        <button on:click={goTop} class="animate-bounce ml-auto rounded-full bg-black
        text-red-500 px-5 sm:px-4 h-5 sm:h-20 hover:bg-black cursor-pointer ">
          <i class=" fa-solid fa-arrow-up grid place-items-center aspect-square" />
        </button>
      </div>
      <Header y={y}/>
      <slot />
      <Footer/>
  </div>

  <svelte:window bind:scrollY={y} bind:innerHeight bind:innerWidth />
