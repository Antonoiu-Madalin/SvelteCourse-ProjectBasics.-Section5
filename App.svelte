<script>
  import Header from "./UI/Header.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";

  let title = "";
  let subtitle = "";
  let address = "";
  let email = "";
  let description = "";
  let imageUrl = "";

  let meetups = [
    {
      id: "m1",
      title: "Coding Bootcamp",
      subtitle: "Learn to code in 2 hours",
      description:
        "In this meetup, we will have some experts that teach you how to code!",
      imageUrl:
        "https://upload.wikimedia.org/wikipedia/commons/thumb/9/9a/Caffe_Nero_coffee_bar%2C_High_St%2C_Sutton%2C_Surrey%2C_Greater_London.JPG/800px-Caffe_Nero_coffee_bar%2C_High_St%2C_Sutton%2C_Surrey%2C_Greater_London.JPG",
      address: "27th Nerd Road, 32523 New York",
      contactEmail: "code@test.com"
    },
    {
      id: "m2",
      title: "Swim Together",
      subtitle: "Let's go for some swimming",
      description: "We will simply swim some rounds!",
      imageUrl:
        "https://upload.wikimedia.org/wikipedia/commons/thumb/6/69/Olympic_swimming_pool_%28Tbilisi%29.jpg/800px-Olympic_swimming_pool_%28Tbilisi%29.jpg",
      address: "27th Nerd Road, 32523 New York",
      contactEmail: "swim@test.com"
    }
  ];

  function addMeetup() {
    const newMeetup = {
      id: Math.random().toString(),
      title: title,
      subtitle: subtitle,
      address: address,
      contactEmail: email,
      description: description,
      imageUrl: imageUrl
    };

    meetups = [newMeetup, ...meetups];
  }
</script>


<style>
  main {
    margin-top: 3rem;
  }
</style>

<Header />

<main>

  <form on:submit|preventDefault={addMeetup}>

    <div class="form-control">
      <label for="title">Title</label>
      <input for="text" id="title" bind:value={title} />
    </div>

    <div class="form-control">
      <label for="suvtitle">Subtitle</label>
      <input for="text" id="subtitle" bind:value={subtitle} />
    </div>

    <div class="form-control">
      <label for="adress">Adress</label>
      <input for="text" id="adress" bind:value={address}/>
    </div>

    <div class="form-control">
      <label for="imageUrl">ImageUrl</label>
      <input for="text" id="imageUrl" bind:value={imageUrl} />
    </div>

    <div class="form-control">
      <label for="email">E-Mail</label>
      <input for="email" id="email" bind:value={email} />
    </div>

    <div class="form-control">
      <label for="description">Description</label>
      <textarea rows="3" id="description" bind:value={description} />
    </div>

    <button type="submit">Save</button>
  </form>

  <MeetupGrid {meetups} />
</main>

