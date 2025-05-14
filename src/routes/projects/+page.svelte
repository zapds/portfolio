<script>
    import avatar from "$lib/assets/avatar.png"
    import apolloLogo from "$lib/assets/apollo_logo.png"
    import hashpayLogo from "$lib/assets/hashpay_logo.png"
</script>

<div class="pt-4 font-mono">
    <h1 class="pt-4 font-mono font-semibold text-2xl text-center">Projects</h1>
    <div class="flex flex-col items-center">
        <div class="flex items-center group p-4 m-4 gap-4 rounded-md border border-border hover:border-white transition-colors duration-300 w-96">
            <img src={apolloLogo} alt="avatar" class="rounded-full group-hover:border group-hover:border-white bor transition-colors duraiton-300 h-12 w-12 ml-2">
            <div class="flex flex-col">
                <a href="https://apollo-bot.xyz" class="font-bold hover:underline">Apollo Bot (sold)</a>
                <p>A utility Discord bot</p>
            </div>

        </div>
        <div class="flex items-center group p-4 m-4 gap-4 rounded-md border border-border hover:border-white transition-colors duration-300 w-96">
            <img src={avatar} alt="avatar" class="rounded-full group-hover:border group-hover:border-white transition-colors duraiton-300 h-12 w-12 ml-2">
            <div class="flex flex-col">
                <a href="https://github.com/zapds/flexifeed" class="font-bold hover:underline">FlexiFeed</a>
                <p>A news aggregator built with sveltekit, tailwind and other stuff</p>
            </div>

        </div>
        <div class="flex items-center group p-4 m-4 gap-4 rounded-md border border-border hover:border-white transition-colors duration-300 w-96">
            <img src={hashpayLogo} alt="avatar" class="rounded-full group-hover:border group-hover:border-white transition-colors duraiton-300 h-12 w-12 ml-2">
            <div class="flex flex-col">
                <a href="https://hashpaybot.xyz" class="font-bold hover:underline">HashPay (in development)</a>
                <p>A Discord bot that provides utilities for crypto payments</p>
            </div>

        </div>
        <div class="flex items-center group p-4 m-4 gap-4 rounded-md border border-border hover:border-white transition-colors duration-300 w-96">
            <img src={avatar} alt="avatar" class="rounded-full group-hover:border group-hover:border-white transition-colors duraiton-300 h-12 w-12 ml-2">
            <div class="flex flex-col">
                <a href="https://github.com/zapds" class="font-bold hover:underline">CrowdSense (in development)</a>
                <p>A non-intrusive IoT device that can estimate the crowd density in public places</p>
            </div>

        </div>
    </div>
</div>