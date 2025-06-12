<script>
  import "../app.pcss";
  import { Button } from "$lib/components/ui/button";
  import { onMount, onDestroy } from "svelte";
  import { spring } from "svelte/motion";

  let coords = spring(
    { x: 0, y: 0 },
    {
      stiffness: 0.1,
      damping: 1,
    },
  );

  function updateMousePosition(event) {
    coords.set({ x: event.clientX, y: event.clientY });
  }

  let homeText = "Home";
  let projectsText = "Projects";
  let statsText = "Stats";
  let blogText = "Blog";

  function randomChar() {
    let chars =
      "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";
    return chars.charAt(Math.floor(Math.random() * chars.length));
  }

  async function changeText(text, setText) {
    let initial = text;
    for (let i = 1; i <= text.length; i++) {
      setText(
        initial.substring(0, i - 1) + randomChar() + initial.substring(i),
      );
      await new Promise((resolve) => setTimeout(resolve, 50)); // Adjust delay as needed
    }
    setText(initial);
  }

  function changeHomeText() {
    changeText("Home", (newText) => (homeText = newText));
  }

  function changeProjectsText() {
    changeText("Projects", (newText) => (projectsText = newText));
  }

  function changeStatsText() {
    changeText("Stats", (newText) => (statsText = newText));
  }

  function changeBlogText() {
    changeText("Blog", (newText) => (blogText = newText));
  }

  if (typeof window !== "undefined") {
    onMount(() => {
      window.addEventListener("mousemove", updateMousePosition);
    });

    onDestroy(() => {
      window.removeEventListener("mousemove", updateMousePosition);
    });
  }
</script>

<div class="bg-[#020817] h-screen w-screen absolute z-[-5]"></div>

<div
  class="radial-bg h-screen w-screen absolute z-[-5]"
  style="--x: {$coords.x}px; --y: {$coords.y}px;"
></div>

<div class="h-screen w-screen grid-bg absolute z-[-5]"></div>

<div class="overflow-hidden box-border w-screen h-screen">
  <div
    class="z-4 sticky backdrop-saturate-150 backdrop-blur-xl flex flex-row min-h-12 border-b border-b-border max-w-screen gap-2 md:gap-24 justify-center"
  >
    <!-- svelte-ignore a11y-no-static-element-interactions -->
    <div class="my-auto" on:mouseenter={changeHomeText}>
      <Button
        class="my-auto flex items-center justify-center font-mono"
        variant="outline"
        href="/"
      >
        {homeText}
      </Button>
    </div>
    <!-- svelte-ignore a11y-no-static-element-interactions -->
    <div class="my-auto" on:mouseenter={changeProjectsText}>
      <Button
        class="my-auto flex items-center justify-center font-mono"
        variant="outline"
        href="/projects"
      >
        {projectsText}
      </Button>
    </div>
    <!-- svelte-ignore a11y-no-static-element-interactions -->
    <div class="my-auto" on:mouseenter={changeStatsText}>
      <Button
        class="my-auto flex items-center justify-center font-mono"
        variant="outline"
        href="/stats"
      >
        {statsText}
      </Button>
    </div>
    <!-- svelte-ignore a11y-no-static-element-interactions -->
    <div class="my-auto" on:mouseenter={changeStatsText}>
      <Button
        class="my-auto flex items-center justify-center font-mono"
        variant="outline"
        href="https://blog.zapdos.me"
      >
        {blogText}
      </Button>
    </div>
  </div>

  <slot class="z-4"></slot>
</div>

<style>
  .radial-bg {
    background: radial-gradient(
      circle 100px at var(--x) var(--y),
      #1e293b,
      transparent
    );
  }
  .grid-bg {
    background-image: url("/src/lib/assets/grids.svg");
  }
</style>
