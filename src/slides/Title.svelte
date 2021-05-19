<script>
    import { onMount } from 'svelte';

    let title;
    onMount(() => {
        let timeout;
        title = new Promise(resolve => {
            timeout = setTimeout(() => resolve('Whats nice together?'), 1000);
        });
        () => clearTimeout(timeout);
    });
</script>

<section>
    <h2>
        {#await title}
            Wait a sec...
        {:then result}
            {result}
        {/await}
    </h2>
</section>
