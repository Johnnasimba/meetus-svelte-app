<script>
	import { createEventDispatcher } from 'svelte'
	import Button from '../UI/Button.svelte'
	import Badge from '../UI/Badge.svelte'

	export let id
  export let title
  export let subtitle
  export let description
  export let imageUrl
	export let email
	export let address
	export let isFav

	const dispatch = createEventDispatcher()
</script>

<style>
  article {
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    border-radius: 5px;
    background: white;
    margin: 1rem;
  }

  header,
  .content,
  footer {
    padding: 1rem;
  }

  .image {
    width: 100%;
    height: 14rem;
  }

  .image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  h1 {
    font-size: 1.25rem;
    margin: 0.5rem 0;
    font-family: "Roboto Slab", sans-serif;
  }

  h1.is-favorite {
    background: #01a129;
    color: white;
    padding: 0 0.5rem;
    border-radius: 5px;
  }

  h2 {
    font-size: 1rem;
    color: #808080;
    margin: 0.5rem 0;
  }

  p {
    font-size: 1.25rem;
    margin: 0;
  }
	.content {
		min-height: 4rem;
	}

</style>
<article>
	<header>
		<h1>{title}
			{#if isFav}
				<Badge>Favorite</Badge>
			{/if}
		</h1>
		<h2>{subtitle}</h2>
		<p>{address}</p>
	</header>
	<div class="image">
		<img src={imageUrl} alt="sample profile" >
	</div>
	<div class="content">
		<p>{description}</p>
	</div>
	<footer>
		<Button href="mailto:{email}" type="button">Contact</Button>
		<Button
			mode="outline"
			color={isFav ? null : 'success'}
			type="button"
			on:click={() => dispatch('toggleFavorite', id)}
		>
			{isFav ? 'Unfavorite' : 'Favorite'}
		</Button>
		<Button type="button">
			Show Details
		</Button>
	</footer>
</article>