<script>
import CustomInput from "./CustomInput.svelte";
import Toggle from "./Toggle.svelte";
let val = "MAX";
let selectedOption = 1;
let price = 0;
let agreed;
let favColor = 'red';
let singleFavColor='red';
let usernameInput='';
let someDiv='';
let customInput='';

$: console.log(val);
$: console.log(selectedOption);
$: console.log(agreed);
$: console.log(favColor);
$: console.log(singleFavColor);
$: console.log(customInput);


function setValue(event) {
    val = event.target.value
}

function saveData(){
	console.log(usernameInput.value);
	console.dir(usernameInput)
	console.dir(someDiv)
	customInput.empty();
	// console.log(document.querySelector('#username').value);
}
</script>

<!-- <input type="text" value={val} on:input={setValue}> -->
<!-- <input type="text" bind:value={val}> -->
<CustomInput bind:val={val} bind:this={customInput}/>
    <Toggle bind:chosenOption={selectedOption}></Toggle>
    <input
        type="number"
        value={price}
        on:input={event=>console.log(event.target.value)}/>

    <label>
        <input
            type ="checkbox"
            bind:checked={agreed}
        >Agree to terms?
    </label>

    <h1> Choose a color</h1>
    <label>
        <input type="radio" name="color" value="green" bind:group={favColor}>Green
		<!--Can change from the type radio to check to make multiple checkbox-->
    </label>
    <label>
        <input type="radio" name="color" value="red" bind:group={favColor}>Red
    </label>
    <label>
        <input type="radio" name="color" value="yellow" bind:group={favColor}>Yellow
    </label>

	<select bind:value={singleFavColor}>
		<option value="green">Green</option>
		<option value="red">Red</option>
	</select>

	<input 
	type="text" id="username" bind:this={usernameInput}>
	<button on:click={saveData}>Save</button>
	<div bind:this={someDiv}></div>
