<script>
  import { serverUrl } from "../../lib/index.js";
  import { goto } from "$app/navigation";

  let firstname, lastname;
  let patientDetails = {
    name: "",
    address: "",
    phone: "",
    dob: "",
    age: "",
    gender: "",
  };

  //function to make name first letter capital
  const captialName = (fullName) => {
    let names = fullName.split(" ");
    let capitalizedNames = [];
    for (let name of names) {
      capitalizedNames.push(
        name.charAt(0).toUpperCase() + name.slice(1).toLowerCase()
      );
    }
    return capitalizedNames.join(" ");
  };
  const captialAddress = (address) => {
    let value = address.split(" ");
    let capitalizedAddress = [];
    for (let name of value) {
      capitalizedAddress.push(
        name.charAt(0).toUpperCase() + name.slice(1).toLowerCase()
      );
    }
    return capitalizedAddress.join(" ");
  };

  const resetform = () => {
    patientDetails = {
      name: "",
      address: "",
      phone: "",
      dob: "",
      age: "",
      gender: "",
    };
  };

  // onsubmit
  const createpatient = async (e) => {
    e.preventdefult;
    patientDetails.name = firstname + " " + lastname;
    let fullName = patientDetails.name;
    patientDetails.name = captialName(fullName);
    let address = patientDetails.address;
    patientDetails.address = captialAddress(address);
    patientDetails.age = parseInt(patientDetails.age);
    // sending data to database
    const res = await fetch(serverUrl + "/patients", {
      headers: [["Content-Type", "application/json"]],
      method: "POST",
      body: JSON.stringify(patientDetails),
    });
    const parsedRes = await res.json();
    if (!parsedRes.errors) {
      resetform();
      goto("/view");
    }
  };
</script>

<!-- Container -->
<div class="container mx-auto mt-10">
  <div
    class="w-auto justify-center items-center flex flex-wrap gap-5 bg-base-200 rounded-lg"
  >
    <div class="avatar p-6">
      <div class="rounded-sm shadow-lg w-auto">
        <img src="/patientform.jpg" alt="patientfillingform" />
      </div>
    </div>
    <div>
      <h3 class="pb-4 font-bold text-2xl text-center">Enter your details</h3>
      <!-- patient form  -->

      <form
        class="px-8 pt-6 pb-8 mb-4 bg-base-100 rounded"
        on:submit={createpatient}
        id="my-form"
      >
        <div class="mb-4 md:flex md:justify-between">
          <div class="mb-4 md:mr-2 md:mb-0">
            <label class="block mb-2 text-sm font-bold" for="firstName">
              First Name
            </label>
            <input
              bind:value={firstname}
              class="input input-bordered focus:input-primary"
              id="firstName"
              type="text"
              placeholder="First Name"
              required
            />
          </div>
          <div class="md:ml-2">
            <label class="block mb-2 text-sm font-bold" for="lastName">
              Last Name
            </label>
            <input
              bind:value={lastname}
              class="input input-bordered focus:input-primary"
              id="lastName"
              type="text"
              placeholder="Last Name"
              required
            />
          </div>
        </div>

        <div class="mb-4 md:flex md:justify-between">
          <div class="mb-4 md:mr-2 md:mb-0">
            <label class="block mb-2 text-sm font-bold" for="addess">
              Address
            </label>
            <input
              bind:value={patientDetails.address}
              class="input input-bordered focus:input-primary"
              id="address"
              type="text"
              name="p_address"
              required
            />
          </div>
          <div class="md:ml-2">
            <label class="block mb-2 text-sm font-bold" for="phonenumber">
              Phone number
            </label>
            <input
              bind:value={patientDetails.phone}
              class="input input-bordered focus:input-primary"
              id="p-phonenumber"
              type="tel"
              name="p-phonenumber"
              required
            />
          </div>
        </div>
        <div class="mb-4 md:flex md:justify-between">
          <div class="mb-4 md:mr-2 md:mb-0">
            <label class="block mb-2 text-sm font-bold" for="dob"> DOB </label>
            <input
              bind:value={patientDetails.dob}
              class="input input-bordered focus:input-primary"
              id="p-dob"
              type="date"
              name="p-dob"
              required
            />
          </div>
          <div class="mb-4 md:mr-2 md:mb-0">
            <label class="block mb-2 text-sm font-bold" for="age"> Age </label>
            <input
              bind:value={patientDetails.age}
              class="input input-bordered focus:input-primary"
              id="p-age"
              type="text"
              name="p-age"
              required
            />
          </div>
        </div>
        <div class="flex flex-col">
          <h1 class="block mb-2 text-sm font-bold">Gender</h1>

          <div class="gender my-2 flex items-center gap-4">
            <label for="male"> Male </label>
            <input
              bind:group={patientDetails.gender}
              class="radio"
              type="radio"
              name="gender"
              value="MALE"
              required
            />

            <label for="female"> Female </label>
            <input
              bind:group={patientDetails.gender}
              type="radio"
              class="radio"
              name="gender"
              value="FEMALE"
              required
            />

            <label for="other" class="mx-2"> Other </label>
            <input
              bind:group={patientDetails.gender}
              type="radio"
              name="gender"
              class="radio"
              value="OTHERS"
              required
            />
          </div>
        </div>

        <div class="mb-6 text-center my-3">
          <button class="btn btn-primary w-full" type="submit" value="submit">
            Submit
          </button>
        </div>
        <div class="text-center text-xl text-neutral-content">
          <span class=""> Health is wealth! </span>
        </div>
      </form>
    </div>
  </div>
</div>
