<script>

    import { onMount } from 'svelte'  
    import Links from './Links.svelte'

    export let headlines = []

   // const env = process.env.KEY

   // @ts-ignore
   const key = import.meta.env.VITE_KEY 
   

    const url = `http://api.mediastack.com/v1/news?access_key=${key}&languages=en&&categories=technology`  

    onMount( async () => {  

        const res = await fetch(url)    
        const newsData = await res.json()    
        headlines = newsData.data   
        console.log(newsData.data)   

    })

    //Does the same thing as the above but on an event

	// let testFunc = async () => {
	// 	const res = await fetch(url1) 
	// 	console.log(res)
	// 	const data = await res.json()  
	// 	people1 = data
	// 	name1 = data[0].name    
	// 	console.log(res)
	// 	console.log(process.env.KEY)
	// }

</script>

<div>
    <Links/>
    {#each headlines as headline (headline.url)}
        <div id="headline">
            <img src={headline.image} alt="">
            <h2>{headline.title}</h2>    
            <h5>{headline.description}</h5>  
            <a href={headline.url} target='blank'>Read More</a>   
            
        </div>
    {/each}
</div>

<style>
    div {
        margin-bottom: 50px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        
    }

    #headline {
        border: .3px solid lightgray;
        padding: 40px;
        border-radius: 15px;
        background-color: whitesmoke;
        margin-top: 35px;
    }

    img {
        max-height: 50vh;
        max-width: 30vw;
        border-radius: 10px;
        margin-bottom: 15px;
    }

    h4 {
        padding-inline: 45px;
    }

    h1 {
        margin-bottom: 65px;
        border: black 1px solid;
        padding: 15px;
        border-radius: 35px;
        background-color: white;
    }

    
</style>