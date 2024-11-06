<script>
import Header from "./UI/Header.svelte";
// import MeetupsItem from "./Meetups/MeetupsItem.svelte";
import MeetupGrid from "./Meetups/MeetupGrid.svelte";

let title = '';
let sub = '';
let des = '';
let imageUrl = '';

let meetups = [{
        id: "m1",
        title: "Coding Bootcamp",
        sub: "Coding Bootcamp",
        des: "in this meetup, we will have some others thing",
        imageUrl: "https://kidlingoo.com/wp-content/uploads/flowers_name_in_english-980x510.jpg.webp",
        email: "email1@gmail.com"
    },
    {
        id: "m2",
        title: "Coding Bootcamp",
        sub: "Coding Bootcamp",
        des: "in this meetup, we will have some others thing",
        imageUrl: "https://dictionary.cambridge.org/images/thumb/flower_noun_002_14403.jpg?version=6.0.36",
        email: "email2@gmail.com"
    }

]

function addMeetup() {
    let newMeetup={
        id: Math.random().toString(),
        title: title,
        sub: sub,
        des: des,
        imageUrl: imageUrl
    };

    // meetups.push(newMeetup) //DOES NOT WORK -> not update the dom , not work for svelte -> use js
    meetups=[...meetups, newMeetup];
}
</script>

<style>
main {
    margin-top: 5rem;
}
</style>

<Header/>
    <main>
        <form on:submit|preventDefault="{addMeetup}">
            <div class="form-control">
                <label for="title">Title</label>
                <input type="text" id="title" bind:value={title}/>
            </div>
            <div class="form-control">
                <label for="sub">Sub</label>
                <input type="text" id="sub" bind:value={sub}/>
            </div>
            <div class="form-control">
                <label for="imageUrl">Image URL</label>
                <input type="text" id="imageUrl" bind:value={imageUrl}/>
            </div>
            <div class="form-control">
                <label for="des">Description</label>
                <textarea rows="3" id="des" bind:value={des}/>
                    </div>
                    <button>Submit</button>
                    </form>
                    <MeetupGrid meetups={meetups}/>
                        </main>
