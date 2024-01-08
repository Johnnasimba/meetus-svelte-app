<script>
	import { createEventDispatcher} from 'svelte'
  import TextInput from '../UI/TextInput.svelte'
	import Button from '../UI/Button.svelte'
	import Modal from '../UI/Modal.svelte'
	import {isEmpty} from '../helpers/validation'

  let title = ''
	let subtitle = ''
	let address = ''
	let imageUrl = ''
	let email = ''
	let description = ''

	$: titleValid = !isEmpty(title)
	$: subtitleValid = !isEmpty(subtitle)
	$: addressValid = !isEmpty(address)
	$: imageUrlValid = !isEmpty(imageUrl)
	$: emailValid = !isEmpty(email)
	$: descriptionValid = !isEmpty(description)
	$: formIsValid =
		titleValid &&
		subtitleValid &&
		addressValid &&
		imageUrlValid &&
		emailValid &&
		descriptionValid


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
			valid={titleValid}
			validityMessage='Please enter a valid title'
			value={title}
			on:input={e => title = e.target.value}
		/>
		<TextInput
			label="Subtitle"
			id="subtitle"
			valid={subtitleValid}
			validityMessage='Please enter a valid subtitle'
			value={subtitle}
			on:input={e => subtitle = e.target.value}
		/>
		<TextInput
			label="Address"
			id="address"
			valid={addressValid}
			validityMessage='Please enter a valid address'
			value={address}
			on:input={e => address = e.target.value}
		/>
		<TextInput
			label="Image URL"
			id="image Url"
			valid={imageUrlValid}
			validityMessage='Please enter a valid image url'
			value={imageUrl}
			on:input={e => imageUrl = e.target.value}
		/>
		<TextInput
			label="Email"
			id="email"
			valid={emailValid}
			validityMessage='Please enter a valid email'
			value={email}
			type="email"
			on:input={e => email = e.target.value}
		/>
		<TextInput
			label="Description"
			id="description"
			valid={descriptionValid}
			validityMessage='Please enter a valid description'
			bind:value={description}
			controlType="textarea"
			rows="3"
		/>
	</form>
	<div slot="footer">
		<Button type="button" mode="outline" on:click={cancel}>Cancel</Button>
		<Button type="button" disabled={!formIsValid} on:click={submitForm}>Save</Button>
	</div>
</Modal>