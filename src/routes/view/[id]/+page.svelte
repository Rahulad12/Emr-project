<script>
  import { page } from "$app/stores";
  import { onMount } from "svelte";
  import { serverUrl } from "../../../lib/index";
  import CreateCheckupEntry from "../../../lib/Components/CreateCheckupEntry.svelte";
  import CheckupsList from "../../../lib/Components/CheckupsList.svelte";
  import AverageStats from "../../../lib/Components/AverageStats.svelte";
  let id = $page.params.id;
  let patientData = null;

  onMount(async () => {
    let res = await fetch(serverUrl + "/patients/" + id);
    let pd = await res.json();
    patientData = pd;
  });
</script>

{#if patientData}
  <CreateCheckupEntry bind:patientData />
  <div
    class="stats rounded-tl-none flex flex-wrap sm:flex-nowrap w-full bg-primary text-primary-content"
  >
    <div class="stat">
      <div class="stat-title text-xl text-base-300 font-bold">
        ID: {patientData.id}
      </div>
      <div class="stat-value">{patientData.name}</div>
      <div class="stat-actions flex">
        <button class="btn btn-sm rounded-r-none">Gender</button>
        <button class="btn btn-sm btn-accent rounded-l-none"
          >{patientData.gender}</button
        >
      </div>
      <div class="stat-actions flex">
        <button class="btn btn-sm rounded-r-none">Address</button>
        <button class="btn btn-sm rounded-l-none btn-accent"
          >{patientData.address}</button
        >
      </div>
    </div>

    <div class="stat">
      <div class="stat-title text-xl text-base-300 font-bold">Age</div>
      <div class="stat-value">{patientData.age}</div>
      <div class="stat-actions flex">
        <button class="btn btn-sm rounded-r-none">DOB</button>
        <button class="btn btn-sm btn-accent rounded-l-none"
          >{new Date(patientData.dob).toDateString()}</button
        >
      </div>
      <div class="stat-actions flex">
        <button class="btn btn-sm rounded-r-none">Phone</button>
        <button class="btn btn-sm btn-accent rounded-l-none"
          >{patientData.phone}</button
        >
      </div>
    </div>
  </div>
  <AverageStats bind:id={patientData.id} />
  <CheckupsList bind:id={patientData.id} />
{/if}
