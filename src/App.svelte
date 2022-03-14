<script >
import { faker } from '@faker-js/faker'
import PeopleTable from '../src/components/PeopleTable.svelte'

let people = [];

const makeRandomPeople = () => {
	const avatar = faker.image.avatar();
	const name = faker.name.findName(); // Rowan Nikolaus
	const email = faker.internet.email(); // Kassandra.Haley@erich.biz
	const age = Math.round( (Math.random()*70)+15 );
	people = [...people, {avatar, name, email,age} ]
	return {avatar, name, email,age} // for getting headers
}
for (let i = 0; i <8; i++) {
	makeRandomPeople();
}

const headers =  Object.keys(makeRandomPeople())

/* sortByObjectKey virker nu, men vi prøver med event... fuck jeg er skrald altså :D HOLD UD
function sortByObjectKey(ObjectKeyNumber) {
	console.log(headers)
	console.log('parameter: ', ObjectKeyNumber)
	const objectKey = headers[ObjectKeyNumber]
	console.log('object key: ',objectKey, ' typeof:  ', typeof(objectKey))

	people.sort(function(a,b) {
		const objectKey = headers[ObjectKeyNumber]
		if (a[objectKey] < b[objectKey]) {
			console.log('-1')
			return -1;
		}
		if (a[objectKey] > b[objectKey]) {
			console.log('+1')
			return 1;
		}
		else {	
			console.log()
			console.log(a[objectKey])
			console.log('0')
			return 0;
		}
	}
	)
	people = people;
}
sortByAge(2)
*/

</script>

<main>
	<h1>People table exercise</h1>
	<PeopleTable headers={headers} people={people}> </PeopleTable>
	<p> Livet er en fest, og jeg er glad for at leve.</p>
</main>



<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>