<script>
    const intef = [
        'AC|±|%|/','7|8|9|*','4|5|6|-','1|2|3|+','0|.|C|='
    ]
    var output = 0
    const f = e => {
        if (e == 'C') {
            output = 0
            return
        }
        if (e == '=') {
            output = eval(output)
            return
        }
        if (output == 0) {
            output = e
            return
        }
        output += e
    }
</script>
<table>
    <tr>
        <td colspan=4 class="r">
            {output}
        </td>
    </tr>
{#each intef as i, a}
<tr>
    {#each i.split('|') as j, b}
    <td on:click={() => f(j)} class={`x${a} y${b}`}>
        {j}
    </td>
    {/each}
</tr>
{/each}
</table>

<style>
    :global(body) {
        background-color: rgb(233, 206, 206);
        user-select: none;
    }
    td {
        width: 30px;
        height: 30px;
        background-color: red;
        text-align: center;
        cursor: pointer;
        border-radius: 20px;
        border:solid 2px gray;
        box-shadow: 1px 1px 4px gray;
        color:white;
    }
    td.r {
        text-align: right;
        padding-right: 10px;
    }
    td:hover {
        background-color: rgb(204, 143, 143);
    }
    td.x0, td.y3 {
        background-color: aqua;
        color:black;
    }
    table {
        margin: auto;
    }
</style>