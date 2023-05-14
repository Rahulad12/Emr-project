<script>
  import { onMount } from "svelte";
  import { serverUrl } from "../../lib/index.js";
  import { tweened } from "svelte/motion";
  //array of patients
  let patient_details = [];
  let current_page = 1;
  let fetching = true;
  let progressValue = tweened(0);

  onMount(async () => {
    await fetchPatients(current_page);
  });

  const startProgress = () => {
    let intervalID = setInterval(() => {
      progressValue.update((val) => val + 10);
      if ($progressValue > 100) {
        clearInterval(intervalID);
      }
    }, 500);
    progressValue.set(0);
  };

  async function fetchPatients(page) {
    fetching = true;
    startProgress();
    let grantrequest = await fetch(serverUrl + "/patients?page=" + page);
    patient_details = await grantrequest.json();
    fetching = false;
  }

  const changePage = async (page) => {
    if (patient_details.length !== 20 && page > 0) {
      return;
    } else if (current_page === 1 && page < 0) {
      return;
    }
    current_page += page;
    current_page = Math.max(current_page, 1);
    await fetchPatients(current_page);
  };
</script>

<h1 class="text-center font-bold text-3xl mt-10">Patients List</h1>

<!-- <header class="header flex justify-center mt-10 items-center">
  <div class="mb-3 flex flex-wrap justify-center items-center">
    <div class="relative mb-4 flex w-full flex-wrap items-stretch">
      <input
        type="text"
        class="relative m-0 input input-bordered focus:input-primary rounded-r-none"
        placeholder="Search"
        aria-label="Search"
        aria-describedby="button-addon3"
      />

      <button
        class="relative z-[2] btn rounded-l-none btn-primary"
        type="submit"
        id="button-addon3"
        data-te-ripple-init
      >
        Search
      </button>
    </div>
  </div>
</header> -->

<div class="overflow-x-auto mt-5">
  <table class="table w-full">
    <thead>
      <tr>
        <th scope="col">
          <a href="/create">
            <button
              type="button"
              class="border btn btn-secondary border-solid px-4 py-2"
            >
              Add +
            </button>
          </a></th
        >
        <th scope="col">Name</th>
        <th scope="col">Address</th>
        <th scope="col">Phone number</th>
        <th scope="col">Gender</th>
        <th scope="col">Age</th>
        <th scope="col">DOB</th>
      </tr>
    </thead>

    {#each patient_details as item, index}
      <tbody>
        <tr class:active={index % 2 !== 0}>
          <td>{item.id} </td>
          <td> <a href={"/view/" + item.id}>{item.name}</a></td>
          <td>{item.address}</td>
          <td>{item.phone}</td>
          <td>{item.gender}</td>
          <td> {item.age}</td>
          <td> {new Date(item.dob).toLocaleDateString()}</td>
        </tr>
      </tbody>
    {/each}
  </table>
</div>
{#if fetching}
  <div class="w-full flex justify-center items-center">
    <div
      class="radial-progress text-secondary"
      style="--value:{$progressValue};"
    />
  </div>
{/if}
<div class="btn-group grid grid-cols-2 mt-5">
  <button on:click={() => changePage(-1)} class="btn btn-outline"
    >Previous page</button
  >
  <button on:click={() => changePage(1)} class="btn btn-outline">Next</button>
</div>
