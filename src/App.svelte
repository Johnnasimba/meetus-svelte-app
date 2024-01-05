<script>
  import Header from './UI/Header.svelte';
  import MeetupGrid from './Meetups/MeetupGrid.svelte'

  const meetups = [
    {
      id: 'm1',
			title: 'Coding Bootcamp',
			subtitle: 'Learn to code in 2 hours',
			description: 'In this meetup, we will have some experts that teach you how to code!',
			imageUrl: 'https://images.unsplash.com/photo-1461749280684-dccba630e2f6?q=80&w=2069&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
			address: '27th Nerd Road, 32523 New York',
			contactEmail: 'example@email.com'
		},
		{
			id: 'm2',
			title: 'Swim Together',
			subtitle: "Let's go for some swimming",
			description: 'We will simply swim some rounds!',
			imageUrl: 'https://images.unsplash.com/photo-1560090995-01632a28895b?q=80&w=2069&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
			address: '27th Nerd Road, 32523 New York',
			contactEmail: ''
		},
    {
			id: 'm3',
			title: 'Learn Svelte',
			subtitle: 'Learn Svelte app in 2 hours',
			description: 'In this meetup, we will have some experts that teach you how to code!',
			imageUrl: 'https://images.unsplash.com/photo-1577648188599-291bb8b831c3?q=80&w=2079&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
			address: '27th Nerd Road, 32523 New York',
			contactEmail: 'example@email.com'
		},
		{
			id: 'm4',
			title: 'Kungfu Together',
			subtitle: "Become a Kungfu master in few hours",
			description: 'We will simply swim some rounds!',
			imageUrl: 'https://images.unsplash.com/photo-1526889588514-2e695856df85?q=80&w=2067&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
			address: '27th Nerd Road, 32523 New York',
			contactEmail: 'example@email.com'
		},
    {
			id: 'm5',
			title: 'More than reading',
			subtitle: 'Book recommendation from others',
			description: 'In this meetup, we will meetup with other book lovers and share our favorite books!',
			imageUrl: 'https://images.unsplash.com/photo-1656778669500-7afe7f78c3d0?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
			address: '27th Nerd Road, 32523 New York',
			contactEmail: 'example@email.com'
		},
		{
			id: 'm6',
			title: 'Friends',
			subtitle: 'Make new friends',
			description: 'We will simply swim some rounds!',
			imageUrl: 'https://plus.unsplash.com/premium_photo-1683146516128-68b12cc44af1?q=80&w=1887&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
			address: '27th Nerd Road, 32523 New York',
			contactEmail: 'example@email.com'
		}
	]

</script>

<style>
	main {
		margin-top: 5rem;
	}
</style>

<Header />
<main>
	<MeetupGrid meetups={meetups} />
</main>










