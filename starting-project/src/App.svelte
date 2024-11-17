<script>
import CustomInput from "./CustomInput.svelte";
import Toggle from "./Toggle.svelte";
let val = "MAX";
let selectedOption = 1;
let price = 0;
let agreed;
let favColor = 'red';
let singleFavColor='red';

$: console.log(val);
$: console.log(selectedOption);
$: console.log(agreed);
$: console.log(favColor);
$: console.log(singleFavColor);

function setValue(event) {
    val = event.target.value
}
</script>

<!-- <input type="text" value={val} on:input={setValue}> -->
<!-- <input type="text" bind:value={val}> -->
<CustomInput bind:val={val}/>
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
