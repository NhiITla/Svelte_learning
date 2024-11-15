<script>
import Header from "./UI/Header.svelte";
// import MeetupsItem from "./Meetups/MeetupsItem.svelte";
import MeetupGrid from "./Meetups/MeetupGrid.svelte";
import TextInput from "./UI/TextInput.svelte";
import Button from "./UI/Button.svelte";
import EditMeetup from "./Meetups/EditMeetup.svelte";

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
        email: "email1@gmail.com",
        isFavorite: true
    },
    {
        id: "m2",
        title: "Coding Bootcamp",
        sub: "Coding Bootcamp",
        des: "in this meetup, we will have some others thing",
        imageUrl: "https://dictionary.cambridge.org/images/thumb/flower_noun_002_14403.jpg?version=6.0.36",
        email: "email2@gmail.com",
        isFavorite: false
    }

]

let editMode = null;

function addMeetup(event) {
    let newMeetup = {
        id: Math.random().toString(),
        title: event.detail.title,
        sub: event.detail.sub,
        des: event.detail.des,
        imageUrl: event.detail.imageUrl
    };

    // meetups.push(newMeetup) //DOES NOT WORK -> not update the dom , not work for svelte -> use js
    meetups = [...meetups, newMeetup];
    editMode = null;
}

function toggleFavorite(event) {
    const id = event.detail;
    const updatedMeetup = {
        ...meetups.find(m => (m.id === id))
    };
    updatedMeetup.isFavorite = !updatedMeetup.isFavorite;
    const meetupIndex = meetups.findIndex(m => m.id === id);
    const updatedMeetups = [...meetups];
    updatedMeetups[meetupIndex] = updatedMeetup;
    meetups = updatedMeetups;
}

function cancelEdit(){
    editMode=null;
}
</script>

<style>
main {
    margin-top: 5rem;
}
</style>

<Header/>
    <main>
        <Button
            on:click="{()=>editMode='add'}"
            >New Meetup</Button>
        {#if editMode==="add"}
        <EditMeetup on:save="{addMeetup}" on:cancel={cancelEdit}/>
            {/if}

            <MeetupGrid meetups={meetups} on:toggle-favorite="{toggleFavorite}"/>
                </main>
