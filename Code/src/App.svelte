<script>
import Header from "./UI/Header.svelte";
// import MeetupsItem from "./Meetups/MeetupsItem.svelte";
import MeetupGrid from "./Meetups/MeetupGrid.svelte";
import TextInput from "./UI/TextInput.svelte";
import Button from "./UI/Button.svelte";

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
    let newMeetup = {
        id: Math.random().toString(),
        title: title,
        sub: sub,
        des: des,
        imageUrl: imageUrl
    };

    // meetups.push(newMeetup) //DOES NOT WORK -> not update the dom , not work for svelte -> use js
    meetups = [...meetups, newMeetup];
}
</script>

<style>
main {
    margin-top: 5rem;
}

form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
}
</style>

<Header/>
    <main>
        <form on:submit|preventDefault="{addMeetup}">
            <TextInput
                id="title"
                label="Title"
                type = "Text"
                value={title}
                on:input={event =>(title = event.target.value)} />
            <TextInput
                id="sub"
                label="Sub"
                type = "Text"
                value={sub}
                on:input={event =>(sub = event.target.value)} />
            <TextInput
                id="imageUrl"
                label="Image Url"
                type = "Text"
                value={imageUrl}
                on:input={event =>(imageUrl = event.target.value)} />
            <TextInput
                id="des"
                label="Description"
                controlType = "textarea"
                value={des}
                on:input={event =>(des = event.target.value)} />

            <Button type="submit" caption="Save"/>
                </form>
                <MeetupGrid meetups={meetups}/>
                    </main>
