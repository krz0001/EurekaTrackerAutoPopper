<svelte:head>
	<title>Occult Tracker</title>
</svelte:head>

<div class="flex flex-col justify-center h-full w-full">
    <div class="bg-slate-950 text-center p-20">
        <h1 class="w-fit mx-auto mb-4">
            <a href={`${base}/`} aria-label="Occult Tracker">
                <img src={`${base}/logo.svg`} alt="Occult Tracker" height="80" class="h-20"/>
            </a>
        </h1>
        
        <div class="mb-8 w-fit mx-auto">
            <LanguageSwitcher />
        </div>
        
        <form class="flex flex-row items-center gap-4 max-w-sm w-full mx-auto" onsubmit={handleSubmit}>
            <input type="text" name="trackerId" placeholder="Tracker ID" class="border-b-2 border-white p-2 focus:outline-none flex-1"/>
            <button type="submit" class="bg-white hover:bg-white/80 text-black px-4 py-2 transition-colors duration-200 cursor-pointer">Enter</button>
        </form>
    </div>
</div>

<script>
    import { goto } from '$app/navigation';
    import { base } from '$app/paths';
    import { currentLanguage } from '$lib/stores';
    import LanguageSwitcher from '../components/LanguageSwitcher.svelte';
    
    // on form submit, go to /[trackerId]
    function handleSubmit(event) {
        event.preventDefault();
        const trackerId = event.target.trackerId.value;
        goto(`${base}/${trackerId}`);
    }
</script>