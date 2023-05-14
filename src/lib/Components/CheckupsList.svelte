<script>
  import { onMount } from "svelte";
  import { serverUrl } from "../index";
  import { tweened } from "svelte/motion";

  export let id;
  let fetching = true;
  let progressValue = tweened(0);
  let current_page = 1;

  let checkups = [];

  onMount(async () => {
    fetchCheckups(current_page);
  });

  const startProgress = () => {
    let intervalID = setInterval(() => {
      progressValue.update((val) => val + 10);
      if ($progressValue > 100) {
        clearInterval(intervalID);
      }
    }, 300);
    progressValue.set(0);
  };

  async function fetchCheckups(page = 1) {
    fetching = true;
    startProgress();
    const res = await fetch(serverUrl + "/checkups/" + id);
    const parsedRes = await res.json();
    if (!parsedRes.errors) {
      checkups = parsedRes;
    }
    console.log(checkups);
    fetching = false;
  }
</script>

{#if checkups.length < 1 && fetching}
  <div class="w-full mt-8 flex justify-center items-center">
    <div
      class="radial-progress text-secondary"
      style="--value:{$progressValue};"
    />
  </div>
{:else}
  <div class="overflow-x-auto mt-8">
    <table class="table table-zebra w-full">
      <!-- head -->
      <thead>
        <tr>
          <th>Date of visit</th>
          <th>Body Temperature(°C)</th>
          <th>Oxygen Saturation(%)</th>
          <th>Heart Rate(bpm)</th>
          <th>Systolic BP</th>
          <th>Diastolic BP</th>
          <th>Respiratory Rate</th>
          <th>Remarks</th>
        </tr>
      </thead>
      <tbody>
        {#each checkups as checkup}
          <tr>
            <td>{new Date(checkup.dateOfVisit).toLocaleDateString()}</td>
            <td>{checkup.bodyTemperature}</td>
            <td>{checkup.oxygenSaturation}</td>
            <td>{checkup.heartRate}</td>
            <td>{checkup.sysBloodPressure}</td>
            <td>{checkup.diaBloodPressure}</td>
            <td>{checkup.respiratoryRate}</td>
            <td>{checkup.remarks}</td>
          </tr>
        {/each}
      </tbody>
    </table>
  </div>
{/if}
