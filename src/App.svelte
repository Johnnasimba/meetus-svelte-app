<script>
  import Header from './UI/Header.svelte';
  import MeetupGrid from './Meetups/MeetupGrid.svelte'
	import EditMeetup from './Meetups/EditMeetup.svelte'
  import Button from './UI/Button.svelte'

  let meetups = [
    {
      id: 'm1',
			title: 'Coding Bootcamp',
			subtitle: 'Learn to code in 2 hours',
			description: 'In this meetup, we will have some experts that teach you how to code!',
			imageUrl: 'https://images.unsplash.com/photo-1461749280684-dccba630e2f6?q=80&w=2069&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
			address: '27th Nerd Road, 32523 New York',
			contactEmail: 'example@email.com',
      isFavorite: false
		},
		{
			id: 'm2',
			title: 'Swim Together',
			subtitle: "Let's go for some swimming",
			description: 'We will simply swim some rounds!',
			imageUrl: 'https://images.unsplash.com/photo-1560090995-01632a28895b?q=80&w=2069&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
			address: '27th Nerd Road, 32523 New York',
			contactEmail: 'test@example.com',
      isFavorite: false
		},
    {
			id: 'm3',
			title: 'Learn Svelte',
			subtitle: 'Learn Svelte app in 2 hours',
			description: 'In this meetup, we will have some experts that teach you how to code!',
			imageUrl: 'https://images.unsplash.com/photo-1577648188599-291bb8b831c3?q=80&w=2079&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
			address: '27th Nerd Road, 32523 New York',
			contactEmail: 'example@email.com',
      isFavorite: false
		},
		{
			id: 'm4',
			title: 'Kungfu Together',
			subtitle: "Become a Kungfu master in few hours",
			description: 'We will simply swim some rounds!',
			imageUrl: 'https://images.unsplash.com/photo-1526889588514-2e695856df85?q=80&w=2067&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
			address: '27th Nerd Road, 32523 New York',
			contactEmail: 'example@email.com',
      isFavorite: false
		},
    {
			id: 'm5',
			title: 'More than reading',
			subtitle: 'Book recommendation from others',
			description: 'In this meetup, we will meetup with other book lovers and share our favorite books!',
			imageUrl: 'https://images.unsplash.com/photo-1656778669500-7afe7f78c3d0?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
			address: '27th Nerd Road, 32523 New York',
			contactEmail: 'example@email.com',
      isFavorite: false

		},
		{
			id: 'm6',
			title: 'Friends',
			subtitle: 'Make new friends',
			description: 'We will simply swim some rounds!',
			imageUrl: 'https://plus.unsplash.com/premium_photo-1683146516128-68b12cc44af1?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
			address: '27th Nerd Road, 32523 New York',
			contactEmail: 'example@email.com',
			isFavorite: false
		}
	]

	let editMode = ''

	function addMeetup (event) {

		const newMeetup = {
      			id: Math.random().toString(),
			title: event.detail.title,
			subtitle: event.detail.subtitle,
			address: event.detail.address,
			imageUrl: event.detail.imageUrl,
			email: event.detail.email,
			description: event.detail.description,
		}

    meetups = [newMeetup, ...meetups]
		editMode = null
	}

  function toggleFavorite(event) {
		const id = event.detail
		const updatedMeetup = { ...meetups.find(m => m.id === id)}
		updatedMeetup.isFavorite = !updatedMeetup.isFavorite
		const meetupIndex = meetups.findIndex(m => m.id === id)
		const updatedMeetups = [...meetups]
		updatedMeetups[meetupIndex] = updatedMeetup
		meetups = updatedMeetups
	}

</script>

<style>
	main {
		margin-top: 5rem;
	}
	.meetup-controls {
		margin: 1rem;
	}
</style>

<Header />
<main>
	<div class="meetup-controls">
		<Button on:click={() => editMode = 'add'} caption="Add Meetup" />
	</div>
	{#if editMode === 'add'}
		<EditMeetup on:save={addMeetup} on:cancel={() => editMode = ''}/>
	{/if}
		<MeetupGrid meetups={meetups} on:toggleFavorite={toggleFavorite}/>


</main>










