<script>
import Icon from 'svelte-awesome';
// import { getContext } from 'svelte';
import Dialog from './Dialog.svelte';
import {edit, checkCircle, minusCircle, plusCircle} from 'svelte-awesome/icons';
export let name= 'Unnamed Counter';
export let value= 0;
let editName= false;
let showOptionMenu = false;

// const { open } = getContext('simple-modal');
function editCounternNameHandler() {
    console.log("edit counter name handler");
}

function decrementHandler() {
    console.log("decrement counter");
    value --;
    if(value<0){
        value = 0;
    }

}

function incrementHandler() {
    console.log("increment handler");
    value++;    
}

function editCounterNameHandler(){
    console.log("inside editCounterNameHanler");
    editName = !editName;
    console.log("editName:", editName);
}

function optionMenuToggleHandler() {
    console.log("clicked optionMenuToggleHandler");
    showOptionMenu = !showOptionMenu;
}
// const showDialog = () => {
// 		open(
// 			Dialog,
// 			{
// 				message: "What is your name?",
// 				hasForm: true,
// 				onCancel,
// 				onOkay
// 			},
// 			{
// 				closeButton: false,
//     		closeOnEsc: false,
//     		closeOnOuterClick: false,
// 			}
// 	  );
// 	};
</script>

<div class="counter">
    <!-- <button on:click={showDialog}>Show a dialog!</button> -->
    <div class="counterName">
        {#if !editName}
            <span>
                {name}
            </span>
            <span on:click={editCounterNameHandler}>
                <Icon data={edit}/>
            </span>
        {:else}
            <input bind:value={name}/>
            <span on:click={editCounterNameHandler}>
                <Icon data={checkCircle}/>
            </span>
        {/if}
    </div>
    <div class="counterValue">{value}</div>
    <div class="counterOptions">
        <span on:click={optionMenuToggleHandler}>...</span>
        {#if showOptionMenu}
        <div class="optionMenu">
            <ul>
                <li>Add/Subtract From Total</li>
                <li>Set Counter To...</li>
                <li>Reset Counter</li>
                <li>Delete Counter</li>
            </ul>
        </div>
        {/if}
    </div>
    <div class="counterButtons">
        <div class="decrementButton">
            <button on:click={decrementHandler}>
                <Icon data={minusCircle}/>
            </button>
        </div>
        <div class="incrementButton">
            <button on:click={incrementHandler}>
                <Icon data={plusCircle}/>
            </button>
        </div>
    </div>
</div>

<style>
li {
    text-decoration: none;
}
.decrementButton{
    float: left;
}
.incrementButton{
    float: right;
}
</style>