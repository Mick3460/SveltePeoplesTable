<script>
    import TableHead from '../components/TableHead.svelte'
    import TableRow from '../components/TableRow.svelte'
    export let headers;
    export let people;
    
    let latestSort = '' ;
    function sort(event){
        const target =event.detail.header;
        //console.log(target)
        if(target !== latestSort){
            latestSort = target;
            people = people.sort(function(a,b){
                if(a[target] < b[target]) return -1;
                if(b[target] > a[target]) return 1;
                return 0;
                })
        } else {
            people = people.reverse()
        }
    }
</script>

<table>    
    <tr>
    <TableHead header={headers} on:myOwnEvent={sort} /> 
    </tr>
    <TableRow people={people} />
</table>

<style>
    table {
        font-family: arial, sans-serif;
        border-collapse: collapse;
        width: 100%;
    }
    tr {
        border: 2px;
    }
</style>