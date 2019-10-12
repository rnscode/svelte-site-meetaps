<script>
	import Header from './Components/UI/Header.svelte';
	import MeetupGrid from './Components/Meetups/MeetupGrid.svelte';


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
		<div class="form-control">
			<label for="title">Title</label>
			<input type="text" id="title" bind:value={title}/>
		</div>
		<div class="form-control">
			<label for="subtitle">Subtitle</label>
			<input type="text" id="subtitle"bind:value={subtitle}/>
		</div>
		<div class="form-control">
			<label for="address">Address</label>
			<input type="text" id="address" bind:value={address}/>
		</div>
		<div class="form-control">
			<label for="imageUrl">Image URL</label>
			<input type="text" id="imageUrl" bind:value={imageUrl}/>
		</div>
		<div class="form-control">
			<label for="email">Email</label>
			<input type="email" id="email" bind:value={contactEmail}/>
		</div>
		<div class="form-control">
			<label for="description">Description</label>
			<textarea rows="3" id="description" bind:value={description}/>
		</div>
		<button type="submit">Save</button>
	</form>

	<MeetupGrid {meetups} />
</main>