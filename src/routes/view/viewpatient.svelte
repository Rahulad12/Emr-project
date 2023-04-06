<script>
    import { onMount } from "svelte";
    //array of patients
    let patient_details = [];

    onMount(async () => {
        let grantrequest = await fetch("http://54.64.108.224:8080/patients");
        patient_details = await grantrequest.json();
    });
</script>

<h1 class="text-center text-2xl my-6">Patients List</h1>
<header class="header flex justify-center pt-2 items-center">
    <div class="mb-3 xl:w-96">
        <div class="relative mb-4 flex w-full flex-wrap items-stretch">
            <input
                type="search"
                class="relative m-0 -mr-px block w-[1%] min-w-0 flex-auto rounded-l border border-solid border-neutral-300 bg-transparent bg-clip-padding px-3 py-1.5 text-base font-normal text-neutral-700 outline-none transition duration-300 ease-in-out focus:border-primary-600 focus:text-neutral-700 focus:shadow-te-primary focus:outline-none dark:border-neutral-600 dark:text-neutral-200 dark:placeholder:text-neutral-200"
                placeholder="Search"
                aria-label="Search"
                aria-describedby="button-addon3"
               
            />

            <!--Search button-->
            <button
                class="relative z-[2] rounded-r border-2 border-primary px-6 py-2 text-xs font-medium uppercase text-primary transition duration-150 ease-in-out hover:bg-black hover:bg-opacity-5 focus:outline-none focus:ring-0"
                type="button"
                id="button-addon3"
                data-te-ripple-init
            >
                Search
            </button>
        </div>
    </div>
</header>
<section class="section flex flex-col justify-center items-center">
    <div class="container flex justify-center flex-wrap p-4">
        {#each patient_details as item}
            <div
                class="card flex border-solid border-2 m-3 p-2 w-fit shadow-inner"
            >
                <ul class="flex flex-col border-solid">
                    <li>Name: <a href="/#"> {item.name}</a></li>
                    <li>Address: {item.address}</li>
                    <li>Phone number: {item.phone}</li>
                    <li>Gender: {item.gender}</li>
                    <li>Age: {item.age}</li>
                    <li>Date of birth: {item.dob}</li>

                    <br />
                </ul>
            </div>
        {/each}
    </div>
</section>
