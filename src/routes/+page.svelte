<script>
    const intef = [
        'C|±|%|/','7|8|9|*','4|5|6|-','1|2|3|+','0|.|='
    ]
    var output = 0
    const f = e => {
        if (e == 'C') {
            output = 0
            return
        }
        if (e == '±') {
            output = -output
            return
        }
        if (e == '%') {
            output = output / 100
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
        <th colspan=4 class="r">
            {output}
        </th>
    </tr>
{#each intef as i, a}
<tr>
    {#each i.split('|') as j, b}
    <td on:click={() => f(j)} class={`x${a} y${b}`}
        colspan={a==4 && b==2 ? 2 : 1}>
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
    th {
        background-color: rgb(197, 223, 233);
        border-radius: 12px;
        border:solid 2px gray;
        box-shadow: 1px 1px 4px gray;
        color:rgb(40, 74, 149);
        text-align: right;
        padding: 5px;
        padding-right: 10px;
        font-size: 20px;
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
    td:hover {
        background-color: rgb(204, 143, 143);
    }
    td.x0, td.y3 {
        background-color: aqua;
        color:black;
    }
    td.x0:hover, td.y3:hover {
        background-color: rgb(120, 181, 181);
        color:black;
    }
    table {
        margin: auto;
        border-spacing: 10px;
        background-color: antiquewhite;
        border-radius: 15px;
        box-shadow: 1px 1px 3px inset black;
    }
</style>