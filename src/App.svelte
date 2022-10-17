<script>
    let characters = [];
    let page = 1;

    async function loadCharacters() {
        const response = await fetch(
            `https://rickandmortyapi.com/api/character?page=${page}`
        );
        const data = await response.json();
        characters = data.results;
    }
    loadCharacters();

    function nextPage() {
        page++;
        loadCharacters();
        console.log("pase")
    }
    function previousPage() {
        page--;
        loadCharacters();
    }
</script>

<main>
    <div class="title">
        <h1>Rick And Mory API (svelte)</h1>
    </div>

    <div class="buttons">
        <button on:click={previousPage} disabled={page === 1} >Preview</button>
        <button on:click={nextPage}>Next</button>
    </div>

    {#each characters as character}
        <div>
            <img src={character.image} alt={character.name} />
            <h2>{character.name}</h2>
            <p>{character.species}</p>
        </div>
    {/each}
</main>

<style>
</style>
