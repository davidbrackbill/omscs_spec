<script>
    import { active_sections, clear } from "../lib/state.js";
    const images = {
        "Machine Learning": "/ml.png",
        "Computer Graphics": "/graphics.png",
        Robotics: "/robotics.png",
        "Computing Systems": "/computing-systems.png",
        "Human Computer Interaction": "/hci.png",
        "Interactive Intelligence": "/interactive-intelligence.png",
        Semesters: "/favicon.png",
    };
</script>

<svelte:head>
    {#each Object.values(images) as image}
        <link rel="preload" href={image} as="image" type="image/png" />
    {/each}
</svelte:head>

<div class="h-screen basis-16 shrink p-2 bg-gray-50 drop-shadow-md">
    {#each Object.entries(images) as [key, image]}
        <div
            title={key}
            class="py-4"
            on:click={() => active_sections.toggle(key)}
        >
            <img
                class="opacity-30 hover:opacity-60"
                style={$active_sections.has(key) ? "opacity:1" : ""}
                src={image}
                alt={image}
            />
        </div>
    {/each}
    <div title="Clear all selections" class="flex justify-center">
        <button class="text-sm" on:click={clear}>Clear</button>
    </div>
</div>
