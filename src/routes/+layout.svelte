<script>
    import "../app.pcss";
    import { Button } from "$lib/components/ui/button";
</script>


<!-- <ModeWatcher /> -->

<div class="sticky backdrop-saturate-150 backdrop-blur-xl flex flex-row min-h-12 border-b border-b-border max-w-screen gap-2 md:gap-24 justify-center ">
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
<slot>

</slot>