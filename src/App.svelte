<script>
	let numbers = [1, 2, 3, 4, 5];
	function addNumber(){
		numbers.push(numbers.length + 1);
		numbers = [...numbers];
	}

	$: sum = numbers.reduce((t, n)=> t + n, 0);

    let count = 0;
	$: doubled = count * 2;
	function incrementCount() {
		count += 1;
	}
	$: {
		console.log(`the count is ${count}`);
	}
	$:if(count >= 10) {
		alert('count is dangerously high!');
		count = 0;
	}
</script>

<p>{numbers.join(' + ')} = {sum}</p>

<button on:click={incrementCount}>
	Clicked {count}
	{count === 1 ? 'time' : 'times'}
</button>

<button on:click={addNumber}> Add a number</button>

<p>{count} doubled is {doubled}</p>

<style>
    button {
	color: red;
    }
</style>