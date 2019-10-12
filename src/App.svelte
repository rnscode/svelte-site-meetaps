<script>
	import Header from './Components/UI/Header.svelte';
	import MeetupGrid from './Components/Meetups/MeetupGrid.svelte';
	import TextInput from './Components/UI/TextInput.svelte';

	let title = '';
	let subtitle = '';
	let description = '';
	let imageUrl = '';
	let address = '';
	let contactEmail = '';

	let meetups = [
		{
			id: 'm1',
			title: 'Coding Bootcamp',
			subtitle: 'Learn to code in 2 hours',
			description: 'In this meetup, we will have ......',
			imageUrl: 'https://upload.wikimedia.org/wikipedia/commons/3/3a/Logo-ubuntu_no%28r%29-black_orange-hex.svg',
			address: 'alguma rua aí',
			contactEmail: 'teste@tes.com'
		},
		{
			id: 'm2',
			title: 'Bootcamp JS',
			subtitle: 'Learn to code in 10 hours',
			description: 'In this meetup, we will have JS JS JS......',
			imageUrl: 'https://upload.wikimedia.org/wikipedia/commons/b/b1/Ubuntu_19.04_Desktop.png',
			address: 'alguma rua aí onde tem muito js',
			contactEmail: 'coding@js.com'
		}
	];

	function addMeetup(event) {
		const newMeetup = {
			id: new Date().getTime().toString(),
			title: title,
			subtitle: subtitle,
			description: description,
			imageUrl: imageUrl,
			address: address,
			contactEmail: contactEmail
		}

		console.log(newMeetup);

		meetups = [newMeetup, ...meetups];

		title = '';
		subtitle = '';
		description = '';
		imageUrl = '';
		address = '';
		contactEmail = '';
	}
</script>

<style>
  main {
    margin-top: 5rem;
  }
</style>

<Header/>

<main>
	<form on:submit|preventDefault={addMeetup}>
		<TextInput 
		id="title" 
		label="Title" 
		value={title} 
		type="text"
		on:input={event => (title = event.target.value)}/>

		<TextInput 
		id="subtitle" 
		label="Subtitle" 
		value={subtitle} 
		type="text"
		on:input={event => (subtitle = event.target.value)}/>

		<TextInput 
		id="address" 
		label="Address" 
		value={address} 
		type="text"
		on:input={event => (address = event.target.value)}/>

		<TextInput 
		id="imageUrl" 
		label="Image URL" 
		value={imageUrl} 
		type="text"
		on:input={event => (imageUrl = event.target.value)}/>
		
		<TextInput 
		id="email" 
		label="E-mail" 
		value={contactEmail} 
		type="email"
		on:input={event => (contactEmail = event.target.value)}/>
	
		<TextInput 
		id="description" 
		label="Description" 
		value={description}
		controlType="textarea" 
		rows="3"
		on:input={event => (description = event.target.value)}/>
		
		<button type="submit">Save</button>
	</form>

	<MeetupGrid {meetups} />
</main>