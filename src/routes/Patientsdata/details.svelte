<script>
    import { each } from 'svelte/internal';
import {patient_details} from '../../routes/view/viewpatient.svelte';
</script>
{#each patient_details as item}
    <h1>{item.name}</h1>
{/each}

