<script>
    import "../app.pcss";
    import { Button } from "$lib/components/ui/button";
    import { onMount, onDestroy } from 'svelte';
    import { spring } from 'svelte/motion';

    let coords = spring({x: 0, y: 0}, {
        stiffness: 0.1,
        damping: 1
    });

    function updateMousePosition(event) {
        coords.set({x: event.clientX, y: event.clientY})
    }


    if (typeof window !== 'undefined') {

        onMount(() => {
        window.addEventListener('mousemove', updateMousePosition);
        });

        onDestroy(() => {
        window.removeEventListener('mousemove', updateMousePosition);
        });
    }


</script>

<style>

    .radial-bg {
    background: radial-gradient(circle 100px at var(--x) var(--y), #1E293B, transparent); 
    }
    .grid-bg {
        background-image: url("/src/lib/assets/grids.svg");

    }


</style>

<div class="bg-[#020817] h-screen w-screen absolute z-[-5]">
</div>

<div class="radial-bg h-screen w-screen absolute z-[-5]" style="--x: {$coords.x}px; --y: {$coords.y}px;">
</div>

<div class="h-screen w-screen grid-bg absolute z-[-5]">
</div>

<div class="overflow-hidden box-border w-screen h-screen">
    <div class="z-4 sticky backdrop-saturate-150 backdrop-blur-xl flex flex-row min-h-12 border-b border-b-border max-w-screen gap-2 md:gap-24 justify-center ">
        <Button class="my-auto flex items-center justify-center font-mono" variant="outline" href="/">
            Home
        </Button>
        <Button class="my-auto flex items-center justify-center font-mono" variant="outline" href="/projects">
            Projects
        </Button>
        <Button class="my-auto flex items-center justify-center font-mono" variant="outline" href="/stats">
            Stats
        </Button>
    </div>

    <slot class="z-4">
    
    </slot>
</div>
