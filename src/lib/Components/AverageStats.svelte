<script>
  import { onMount } from "svelte";
  import { serverUrl } from "../index";

  export let id;
  let averageStats = {};
  onMount(async () => {
    const res = await fetch(serverUrl + "/patients/average/" + id);
    const parsedRes = await res.json();
    if (!parsedRes.errors) {
      averageStats = parsedRes;
    }
    console.log();
  });
</script>

{#if averageStats.avgHeartRate >= 0}
  <h1 class="stat-title text-2xl mt-8">Average Statistics</h1>
  <div class="stats flex shadow">
    <div class="stat place-items-center">
      <div class="stat-title">Heart Rate</div>
      <div class="stat-value">{averageStats.avgHeartRate}</div>
    </div>

    <div class="stat place-items-center">
      <div class="stat-title">Respiratory Rate</div>
      <div class="stat-value">{averageStats.avgRespiratoryRate}</div>
    </div>

    <div class="stat place-items-center">
      <div class="stat-title">Systolic BP</div>
      <div class="stat-value">{averageStats.avgSysBloodPressure}</div>
    </div>

    <div class="stat place-items-center">
      <div class="stat-title">Diastolic BP</div>
      <div class="stat-value">{averageStats.avgDiaBloodPressure}</div>
    </div>

    <div class="stat place-items-center">
      <div class="stat-title">Oxygen Saturation</div>
      <div class="stat-value">{averageStats.avgOxygenSaturation}</div>
    </div>

    <div class="stat place-items-center">
      <div class="stat-title">Body Temperature</div>
      <div class="stat-value">{averageStats.avgBodyTemperature}</div>
    </div>
  </div>
{/if}
