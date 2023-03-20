<svelte:head>
	<title>XKCD</title>
	<meta name="description" content="About this app" />
</svelte:head>

<script lang="ts">
    import type { IComic } from "../../interface/IComic";

    const email: string = 'e.stroganov@innopolis.university';

    const getComicId = async (): Promise<number> => {
        let response: Response = await fetch(`https://fwd.innopolis.app/api/hw2?email=${email}`);
        let id: number = await response.json();
        return id;
    };

    const getXKCD = async (): Promise<IComic> => {
        let comicId: number = await getComicId();
        let response: Response = await fetch(`https://getxkcd.vercel.app/api/comic?num=${comicId}`);
        let comic: IComic = await response.json();
        console.log(comic);
        return comic;
    };
</script>

<p>Refresh the page (F5) to see the new comic</p>
<!-- svelte-ignore empty-block -->
{#await getXKCD()}
{:then comic}
<div class="container">
    <div class="image">
        <img id="myImage" src={comic.img} alt={comic.alt}>
    </div>
    <p id="desc" class="comic_desc">
        {comic.alt}
    </p>
</div>
{/await}

