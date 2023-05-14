<script>
  import { serverUrl } from "../index";

  export let patientData;
  let newCheckupEntry = {
    dateOfVisit: "",
    bodyTemperature: "",
    oxygenSaturation: "",
    respiratoryRate: "",
    diaBloodPressure: "",
    sysBloodPressure: "",
    heartRate: "",
    remarks: "",
  };
  const createEntry = async () => {
    console.log(newCheckupEntry);
    newCheckupEntry.patientId = patientData.id;
    const res = await fetch(serverUrl + "/checkups", {
      headers: [["Content-Type", "application/json"]],
      method: "POST",
      body: JSON.stringify(newCheckupEntry),
    });
    const parsedRes = res.json();
    if (!parsedRes.errors) {
      window.location.reload();
    }
  };
</script>

<!-- The button to open modal -->
<a href="#my-modal-2" class="btn btn-primary rounded-b-none mt-10"
  >Create Checkup entry</a
>
<!-- Put this part before </body> tag -->
<div class="modal" id="my-modal-2">
  <div class="modal-box w-11/12 max-w-5xl">
    <h3 class="font-bold text-xl">
      Create checkup entry for {patientData.name}
    </h3>
    <form class="p-8 bg-base-100 rounded" on:submit={createEntry} id="my-form">
      <div class="mb-4 md:flex md:justify-between">
        <div class="mb-4 md:mr-2 md:mb-0">
          <label class="block mb-2 text-sm font-bold" for="dov">
            Date of visit
          </label>
          <input
            bind:value={newCheckupEntry.dateOfVisit}
            class="input input-bordered focus:input-primary"
            type="date"
            id="dov"
            required
          />
        </div>
        <div class="md:ml-2">
          <label class="block mb-2 text-sm font-bold" for="bodyTemperature">
            Body temperature
          </label>
          <input
            bind:value={newCheckupEntry.bodyTemperature}
            class="input input-bordered focus:input-primary"
            min="30.0"
            step="0.1"
            max="45.0"
            id="bodyTemperature"
            type="number"
            placeholder="Body temperature"
            required
          />
        </div>
      </div>

      <div class="mb-4 md:flex md:justify-between">
        <div class="mb-4 md:mr-2 md:mb-0">
          <label class="block mb-2 text-sm font-bold" for="oxySat">
            Oxygen Saturation
          </label>
          <input
            bind:value={newCheckupEntry.oxygenSaturation}
            class="input input-bordered focus:input-primary"
            id="oxySat"
            type="number"
            min="0"
            max="100"
            placeholder="Oxygen Saturation"
            required
          />
        </div>
        <div class="md:ml-2">
          <label class="block mb-2 text-sm font-bold" for="heartRate">
            Heart Rate
          </label>
          <input
            bind:value={newCheckupEntry.heartRate}
            class="input input-bordered focus:input-primary"
            id="heartRate"
            placeholder="Heart Rate"
            min="0"
            max="300"
            type="number"
            required
          />
        </div>
      </div>

      <div class="mb-4 md:flex md:justify-between">
        <div class="mb-4 md:mr-2 md:mb-0">
          <label class="block mb-2 text-sm font-bold" for="sbp">
            Systolic BP
          </label>
          <input
            bind:value={newCheckupEntry.sysBloodPressure}
            class="input input-bordered focus:input-primary"
            id="sbp"
            min="0"
            max="300"
            placeholder="Systolic BP"
            type="number"
            required
          />
        </div>
        <div class="mb-4 md:mr-2 md:mb-0">
          <label class="block mb-2 text-sm font-bold" for="dbp">
            Diastolic BP
          </label>
          <input
            bind:value={newCheckupEntry.diaBloodPressure}
            class="input input-bordered focus:input-primary"
            id="dbp"
            min="0"
            max="300"
            placeholder="Diastolic BP"
            type="number"
            required
          />
        </div>
      </div>

      <div class="mb-4 md:flex md:justify-between">
        <div class="mb-4 md:mr-2 md:mb-0">
          <label class="block mb-2 text-sm font-bold" for="respRate">
            Respiratory Rate
          </label>
          <input
            bind:value={newCheckupEntry.respiratoryRate}
            class="input input-bordered focus:input-primary"
            id="respRate"
            type="number"
            placeholder="Respiratory Rate"
            min="0"
            max="100"
            required
          />
        </div>
        <div class="mb-4 md:mr-2 md:mb-0">
          <label class="block mb-2 text-sm font-bold" for="remarks">
            Remarks
          </label>
          <input
            bind:value={newCheckupEntry.remarks}
            class="input input-bordered focus:input-primary"
            id="remarks"
            type="text"
            placeholder="Remarks"
            required
          />
        </div>
      </div>

      <div class="mt-6 text-center">
        <button class="btn btn-primary w-full" type="submit" value="submit">
          Create
        </button>
      </div>
    </form>
    <div class="modal-action">
      <a href="#" class="btn">Cancel</a>
    </div>
  </div>
</div>
