<script>
    import { text } from "svelte/internal";

</script>

<style>
  .side-image{
    height: fit-content;
    /* border: 2px solid red; */
  }
  .side-image img{
    height: 30rem;
    width: 24rem;
    border-top-left-radius: .5rem;
    border-bottom-right-radius: .5rem;
  }

</style>
<!-- component -->

  <!-- Container -->
  <div class="container mx-auto">
    <div class="flex justify-center px-6 my-12">
      <!-- Row -->
      <div class="w-full xl:w-3/4 lg:w-11/12 flex">
        <!-- Col -->
        <div
          class="side-image">
          <img src="/patientform.jpg" alt="patientfillingform">
        </div>
       
        <!-- Col -->
        <div class="w-full lg:w-7/12 bg-white p-5 rounded-lg lg:rounded-l-none">
          <h3 class="pt-4 text-2xl text-center">Enter your details</h3>
          <!-- patient form  -->

          <form class="px-8 pt-6 pb-8 mb-4 bg-white rounded" method="post">
            <div class="mb-4 md:flex md:justify-between">
              <div class="mb-4 md:mr-2 md:mb-0">
                <label
                  class="block mb-2 text-sm font-bold text-gray-700"
                  for="firstName"
                >
                  First Name
                </label>
                <input
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
                  class="w-full px-3 py-2 text-sm leading-tight text-gray-700 border rounded shadow appearance-none focus:outline-none focus:shadow-outline"
                  id="p-dob"
                  type="date"
                  name="p-dob"
                  required
                />
              </div>
            </div>
            <div class="flex  flex-col">
              <h1 class="block mb-2 text-sm font-bold text-gray-700">
                Gender
              </h1>
              

              <div class="gender my-2">
                <label for="male">
                  Male
                </label>
                <input
                 class="mx-2"
                 type="radio"
                 name="gender"
                 required
                >

                <label for="female">
                  Female
                </label>
                <input
                 type="radio"
                 name="gender"
                 required
                >
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
            <span> Health is  wealth!! </span>
          </form>
        </div>
      </div>
    </div>
  </div>
