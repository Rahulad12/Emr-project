<script>
    import { onMount } from "svelte";
    import { serverUrl } from "../../lib/index.js";
    //array of patients
    let patient_details = [];

    onMount(async () => {
        let grantrequest = await fetch(serverUrl + "/patients");
        patient_details = await grantrequest.json();
    });
   
</script>

<h1 class="text-center text-2xl my-6">Patients List</h1>

<header class="header flex justify-center pt-2 items-center">
    <div class="mb-3 xl:w-96">
        <div class="relative mb-4 flex w-full flex-wrap items-stretch">
            <input
                type="text"
                class="relative m-0 -mr-px block w-[1%] min-w-0 flex-auto rounded-l border border-solid border-neutral-300 bg-transparent bg-clip-padding px-3 py-1.5 text-base font-normal text-neutral-700 outline-none transition duration-300 ease-in-out focus:border-primary-600 focus:text-neutral-700 focus:shadow-te-primary focus:outline-none dark:border-neutral-600 dark:text-neutral-200 dark:placeholder:text-neutral-200"
                placeholder="Search"
                aria-label="Search"
                aria-describedby="button-addon3"
                
            />

            <button
                class="relative z-[2] rounded-r border-2 border-primary px-6 py-2 text-xs font-medium uppercase text-primary transition duration-150 ease-in-out hover:bg-black hover:bg-opacity-5 focus:outline-none focus:ring-0"
                type="submit"
                id="button-addon3"
                data-te-ripple-init
            >
                Search
            </button>
        </div>
    </div>
   
</header> 
<section class="section flex justify-center">
    <div class="container flex justify-center flex-wrap p-4 flex-col w-fit">
        <div class="table">
            <table class="patients-table  border table-auto">
                <thead >
                    <tr
                        class="table_data border border-b bg-neutral-100 dark:border-neutral-500 dark:bg-neutral-700"
                    >
                        <th scope="col" class="px-6 py-4">#</th>
                        <th scope="col" class="px-6 py-4">Name</th>
                        <th scope="col" class="px-6 py-4">Address</th>
                        <th scope="col" class="px-6 py-4">Phone number</th>
                        <th scope="col" class="px-6 py-4">Gender</th>
                        <th scope="col" class="px-6 py-4">Age</th>
                        <th scope="col" class="px-6 py-4">DOB</th>
                        <th scope="col" class="px-6 py-4">
                            <a href="/create">
                                <button
                                    type="button"
                                    class=" bg-green-300 border border-solid  px-4 py-2">
                                    Add +
                                </button>
                            </a></th
                        >
                    </tr>
                </thead>

                {#each patient_details as item}
                    <tbody class="border">

                        <tr>
                            <td class="whitespace-nowrap px-6 py-4">{item.id} </td>
                            <td class="whitespace-nowrap px-6 py-4"
                                > <a href="/Patientsdata">{item.name}</a></td
                            >
                            <td class="whitespace-nowrap px-6 py-4">{item.address}</td>
                            <td class="whitespace-nowrap px-6 py-4"
                                >{item.phone}</td
                            >
                            <td class="whitespace-nowrap px-6 py-4">{item.gender}</td>
                            <td class="whitespace-nowrap px-6 py-4">
                                {item.age}</td
                            >
                            <td class="whitespace-nowrap px-6 py-4"> {item.dob}</td>
                        </tr>
                    </tbody>
                {/each}
            </table>
        </div>
    </div>
</section>

