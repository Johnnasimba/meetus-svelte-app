<script>
	import { createEventDispatcher} from 'svelte'
  import TextInput from '../UI/TextInput.svelte'
	import Button from '../UI/Button.svelte'
	import Modal from '../UI/Modal.svelte'

	let title = ''
	let subtitle = ''
	let address = ''
	let imageUrl = ''
	let email = ''
	let description = ''

	const dispatch = createEventDispatcher()

	function submitForm() {
		const meetupData = {
			title,
			subtitle,
			address,
			imageUrl,
			email,
			description
		}
		dispatch('save', meetupData)
	}

  function cancel () {
		dispatch('cancel')
	}

</script>

<style>
  form {
    width: 100%;
  }
</style>
<Modal title="Add Meetup" on:cancel>
	<form on:submit|preventDefault={submitForm}>
		<TextInput
			label="Title"
			id="title"
			value={title}
			on:input={e => title = e.target.value}
		/>
		<TextInput
			label="Subtitle"
			id="subtitle"
			value={subtitle}
			on:input={e => subtitle = e.target.value}
		/>
		<TextInput
			label="Address"
			id="address"
			value={address}
			on:input={e => address = e.target.value}
		/>
		<TextInput
			label="Image URL"
			id="image Url"
			value={imageUrl}
			on:input={e => imageUrl = e.target.value}
		/>
		<TextInput
			label="Email"
			id="email"
			value={email}
			type="email"
			on:input={e => email = e.target.value}
		/>
		<TextInput
			label="Description"
			id="description"
			value={description}
			controlType="textarea"
			rows="3"
			on:input={e => description = e.target.value}
		/>
	</form>
	<div slot="footer">
		<Button type="button" mode="outline" on:click={cancel}>Cancel</Button>
		<Button type="button"  on:click={submitForm}>Save</Button>
	</div>
</Modal>