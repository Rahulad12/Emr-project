<script>
    import { onMount } from "svelte";
    // import { paginate, LightPaginationNav } from 'svelte-paginate'
    // array of patients
    let patient_details = [
        // {
        //     id: 1,
        //     age: 21,
        //     gender: "FEMALE",
        //     name: "Rahul Adhikari",
        //     address: "Bhaktapur",
        //     phone: "9876543210",
        //     dob: "2001-01-22T00:00:00.000+00:00",
        // },
        // {
        //     id: 2,
        //     age: 20,
        //     gender: "MALE",
        //     name: "Jivan Parajuli",
        //     address: "Imadol",
        //     phone: "9862116777",
        //     dob: "2002-08-30T00:00:00.000+00:00",
        // },
        // {
        //     id: 3,
        //     age: 33,
        //     gender: "MALE",
        //     name: "Ramesh Humagain",
        //     address: "Birtamod",
        //     phone: "9876543210",
        //     dob: "1987-04-02T00:00:00.000+00:00",
        // },
        // {
        //     id: 4,
        //     age: 33,
        //     gender: "MALE",
        //     name: "Ramesh Humagain",
        //     address: "Birtamod",
        //     phone: "9876543210",
        //     dob: "1987-04-02T00:00:00.000+00:00",
        // },
        // {
        //     id: 5,
        //     age: 33,
        //     gender: "MALE",
        //     name: "Ramesh Humagain",
        //     address: "Birtamod",
        //     phone: "9876543210",
        //     dob: "1987-04-02T00:00:00.000+00:00",
        // },
        // {
        //     id: 6,
        //     age: 33,
        //     gender: "MALE",
        //     name: "Ramesh Humagain",
        //     address: "Birtamod",
        //     phone: "9876543210",
        //     dob: "1987-04-02T00:00:00.000+00:00",
        // },
        // {
        //     id: 7,
        //     age: 33,
        //     gender: "MALE",
        //     name: "Ramesh Humagain",
        //     address: "Birtamod",
        //     phone: "9876543210",
        //     dob: "1987-04-02T00:00:00.000+00:00",
        // },
        // {
        //     id: 8,
        //     age: 33,
        //     gender: "MALE",
        //     name: "Ramesh Humagain",
        //     address: "Birtamod",
        //     phone: "9876543210",
        //     dob: "1987-04-02T00:00:00.000+00:00",
        // },
        // {
        //     id: 9,
        //     age: 33,
        //     gender: "MALE",
        //     name: "Ramesh Humagain",
        //     address: "Birtamod",
        //     phone: "9876543210",
        //     dob: "1987-04-02T00:00:00.000+00:00",
        // },
        // {
        //     id: 10,
        //     age: 33,
        //     gender: "MALE",
        //     name: "Ramesh Humagain",
        //     address: "Birtamod",
        //     phone: "9876543210",
        //     dob: "1987-04-02T00:00:00.000+00:00",
        // },
        // {
        //     id: 11,
        //     age: 33,
        //     gender: "MALE",
        //     name: "Ramesh Humagain",
        //     address: "Birtamod",
        //     phone: "9876543210",
        //     dob: "1987-04-02T00:00:00.000+00:00",
        // },
        // {
        //     id: 12,
        //     age: 33,
        //     gender: "MALE",
        //     name: "Ramesh Humagain",
        //     address: "Birtamod",
        //     phone: "9876543210",
        //     dob: "1987-04-02T00:00:00.000+00:00",
        // },
        // {
        //     id: 13,
        //     age: 33,
        //     gender: "MALE",
        //     name: "Ramesh Humagain",
        //     address: "Birtamod",
        //     phone: "9876543210",
        //     dob: "1987-04-02T00:00:00.000+00:00",
        // },
    ];

    onMount( async ()=>{

        let  grantrequest = await fetch('http://54.64.108.224:8080/patients');
        patient_details = await grantrequest.json();
        console.log(patient_data);
    });
</script>
<section class="section flex flex-col justify-center items-center  ">
    <h1 class="text-center  text-2xl mt-6">Patient list</h1>

    <div class="container flex justify-center flex-wrap p-4">
        {#each patient_details as item}
            <div
                class="card flex border-solid border-2 m-3  p-2 w-fit  shadow-inner"
            >
                <ul class="flex flex-col border-solid ">
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
