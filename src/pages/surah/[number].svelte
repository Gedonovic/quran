<script>
    export let number;

    const list = (async () => {
        const response = await fetch(
            "https://quran-endpoint.vercel.app/quran/" + number
        );
        return await response.json();
    })();
</script>

{#await list}
    
{:then data}
    
        
            
                
                    <h1>
                        {#if data.data.preBismillah !== null}
                            {data.data.preBismillah.text.ar}
                        {/if}
                    </h1>
                    <p>
                        {#if data.data.preBismillah !== null}
                            {data.data.preBismillah.text.read}
                        {/if}
                    </p>
                
          
            
                {#each data.data.ayahs as ayat}
                    
                        
                            
                                <h1>
                                    <span>{ayat.text.ar}</span>
                                    <p>{ayat.text.read}</p>
                                </h1>
                                <p>
                                    <span
                                        >{ayat.number.insurah}</span
                                    >{ayat.translation.id}
                                </p>
                                
                        
                    
                {/each}
           
        
    
{:catch error}
    <p>{error}</p>
{/await}

<style>
    img {
        width: 50px;
        height: auto;
    }

    audio {
        width: 300px;
        height: 54px;
    }
</style>
