<script>
    import { each } from "svelte/internal";
    import { Rahul } from "../../lib/check.js";
</script>

<!-- {#each Rahul as item}
    <h1>{item.name}</h1>
{/each} -->
<div class="container border border-zinc-900 w-1/2 mx-auto p-2 my-4">
    <ul class="form_heading flex justify-between px-2">
        <div class="part-1">
            <li class="list-iitem">Name: {Rahul[0].name}</li>
            <li class="list-item">Age: {Rahul[0].age}</li>
        </div>

        <div class="part-2">
            <li class="list-item">Date: {Rahul[0].dob}</li>
            <li class="list-item">Blood-group: {Rahul[0].bg}</li>
        </div>
    </ul>
    <br />
    <!-- form section part -->
    <div class="data-table flex flex-col justify-center ">
        <table class="table-auto">
            <thead>
                <tr class="text-center border border-black">
                    <th scope="col" class="px-10 text-left">Daignosis</th>
                    <th scope="col" class="px-10 text-left">Range</th>
                    <th scope="col" class="px-10 text-left">pateint Data</th>
                </tr>
            </thead>
            <tbody>
                <tr class="border border-black">
                    <td class="px-2 py-2">Body Temperature</td>
                    <td class="px-2 py-2"> 97.9 <span>&deg</span>f to 99 <span>&deg</span>f</td>
                    <td class="px-2 py-2"> undefined</td>
                </tr>
                <tr class="border border-black">
                    <td class="px-2 py-2">Oxygen Saturation</td>
                    <td class="px-2 py-2"> 97 % to 99 %</td>
                    <td class="px-2 py-2"> undefined</td>
                </tr>
                <tr class="border border-black">
                    <td class="px-2 py-2">Respiratory Rate</td>
                    <td class="px-2 py-2"> 12 to 18 </td>
                    <td class="px-2 py-2"> undefined</td>
                </tr>
                <tr class="border border-black">
                    <td class="px-2 py-2">Heart Rate</td>
                    <td class="px-2 py-2"> 55 to 110 </td>
                    <td class="px-2 py-2"> undefined</td>
                </tr>
                <tr class="border border-black">
                    <td class="px-2 py-2">Sys Blood Pressure</td>
                    <td class="px-2 py-2">120 / 20</td>
                    <td class="px-2 py-2"> undefined</td>
                </tr>
                <tr class="border border-black">
                    <td class="px-2 py-2">Dia Blood Pressure</td>
                    <td class="px-2 py-2"> 75 / 15 </td>
                    <td class="px-2 py-2"> undefined</td>
                </tr>

            </tbody>
        </table>
    </div>
    <div class="remarks">
        <p class="text-bold text-justify">
            <spam class="text-lg font-bold">Remarks:</spam> Lorem ipsum dolor sit amet consectetur adipisicing elit. Soluta, necessitatibus. Eveniet provident doloremque optio facere ut quisquam tenetur repellat minima?
        </p>
    </div>
</div>

<style>
    .container
table, th, td {
  border: 1px solid black;
  border-collapse: collapse;
}
</style>