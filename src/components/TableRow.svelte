<script>
    export let people;
</script>

{#each people as person}
    <tr>
    {#each Object.keys(person) as key}  <!-- Object.keys(person) returns an array of all the keys in the object-->
        {#if key.toString() == "avatar"}
            <td> <img src='{person[key]}' alt='Avatar of person' height="80"/> </td>
        {:else}
        <td>{person[key]} </td> <!-- "key" would just give "name" or "email".. We need to specify it's from the person-->
        {/if}
    {/each}
    </tr>
{/each}

<style>
   td {
        border: 1px solid #dddddd;
        text-align: left;
        padding: 8px;
        display: inline-block;
        height: 100px;
        width: 300px;
    }
</style>