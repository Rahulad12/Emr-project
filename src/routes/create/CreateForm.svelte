<script>
  import { bind } from "svelte/internal";
  import {serverUrl} from '../../lib/index.js';

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
    const resquest = await fetch( serverUrl +"/patients", {
      headers: [["Content-Type", "application/json"]],
      method: "POST",
      body: JSON.stringify(patientDetails),
    });
    console.log(patientDetails);
    console.log(resquest);
  };
</script>

<!-- Container -->
<div class="container mx-auto">
  <div class="flex justify-center px-6 my-12">
    <!-- Row -->
    <div class="w-full xl:w-3/4 lg:w-11/12 flex">
      <!-- Col -->
      <div class="side-image">
        <img src="/patientform.jpg" alt="patientfillingform" />
      </div>

      <!-- Col -->
      <div class="w-full lg:w-7/12 bg-white p-5 rounded-lg lg:rounded-l-none">
        <h3 class="pt-4 text-2xl text-center">Enter your details</h3>
        <!-- patient form  -->

        <form
          class="px-8 pt-6 pb-8 mb-4 bg-white rounded"
          on:submit={createpatient}
          id="my-form"
        >
          <div class="mb-4 md:flex md:justify-between">
            <div class="mb-4 md:mr-2 md:mb-0">
              <label
                class="block mb-2 text-sm font-bold text-gray-700"
                for="firstName"
              >
                First Name
              </label>
              <input
                bind:value={firstname}
                class="w-full px-3 py-2 text-sm leading-tight text-gray-700 border rounded shadow appearance-none focus:outline-none focus:shadow-outline"
                id="firstName"
                type="text"
                placeholder="First Name"
                required
              />
            </div>
            <div class="md:ml-2">
              <label
                class="block mb-2 text-sm font-bold text-gray-700"
                for="lastName"
              >
                Last Name
              </label>
              <input
                bind:value={lastname}
                class="w-full px-3 py-2 text-sm leading-tight text-gray-700 border rounded shadow appearance-none focus:outline-none focus:shadow-outline"
                id="lastName"
                type="text"
                placeholder="Last Name"
                required
              />
            </div>
          </div>

          <div class="mb-4 md:flex md:justify-between">
            <div class="mb-4 md:mr-2 md:mb-0">
              <label
                class="block mb-2 text-sm font-bold text-gray-700"
                for="addess"
              >
                Address
              </label>
              <input
                bind:value={patientDetails.address}
                class="w-full px-3 py-2 text-sm leading-tight text-gray-700 border rounded shadow appearance-none focus:outline-none focus:shadow-outline"
                id="address"
                type="text"
                name="p_address"
                required
              />
            </div>
            <div class="md:ml-2">
              <label
                class="block mb-2 text-sm font-bold text-gray-700"
                for="phonenumber"
              >
                Phone number
              </label>
              <input
                bind:value={patientDetails.phone}
                class="w-full px-3 py-2 text-sm leading-tight text-gray-700 border rounded shadow appearance-none focus:outline-none focus:shadow-outline"
                id="p-phonenumber"
                type="tel"
                name="p-phonenumber"
                required
              />
            </div>
          </div>
          <div class="mb-4 md:flex md:justify-between">
            <div class="mb-4 md:mr-2 md:mb-0">
              <label
                class="block mb-2 text-sm font-bold text-gray-700"
                for="dob"
              >
                DOB
              </label>
              <input
                bind:value={patientDetails.dob}
                class="w-full px-3 py-2 text-sm leading-tight text-gray-700 border rounded shadow appearance-none focus:outline-none focus:shadow-outline"
                id="p-dob"
                type="date"
                name="p-dob"
                required
              />
            </div>
            <div class="mb-4 md:mr-2 md:mb-0">
              <label
                class="block mb-2 text-sm font-bold text-gray-700"
                for="age"
              >
                Age
              </label>
              <input
                bind:value={patientDetails.age}
                class="w-full px-3 py-2 text-sm leading-tight text-gray-700 border rounded shadow appearance-none focus:outline-none focus:shadow-outline"
                id="p-age"
                type="text"
                name="p-age"
                required
              />
            </div>
          </div>
          <div class="flex flex-col">
            <h1 class="block mb-2 text-sm font-bold text-gray-700">Gender</h1>

            <div class="gender my-2">
              <label for="male"> Male </label>
              <input
                bind:group={patientDetails.gender}
                class="mx-2"
                type="radio"
                name="gender"
                value="MALE"
                required
              />

              <label for="female"> Female </label>
              <input
                bind:group={patientDetails.gender}
                type="radio"
                name="gender"
                value="FEMALE"
                required
              />

              <label for="other" class="mx-2"> Other </label>
              <input
                bind:group={patientDetails.gender}
                type="radio"
                name="gender"
                value="OTHERS"
                required
              />
            </div>
          </div>

          <div class="mb-6 text-center my-3">
            <button
              class="w-full px-4 py-2 font-bold text-white bg-blue-500 rounded-full hover:bg-blue-700 focus:outline-none focus:shadow-outline"
              type="submit"
            >
              Submit
            </button>
          </div>
          <span> Health is wealth!! </span>
        </form>
      </div>
    </div>
  </div>
</div>

<style>
  .side-image {
    height: fit-content;
    /* border: 2px solid red; */
  }
  .side-image img {
    height: 30rem;
    width: 24rem;
    border-top-left-radius: 0.5rem;
    border-bottom-right-radius: 0.5rem;
  }
</style>
