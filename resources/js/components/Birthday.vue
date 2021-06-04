<template>
    <div class="space-y-4">
        <p>DOB: {{ dob.date }}</p>
        <p>Age: {{ dob.age }}</p>
    </div>
</template>

<script>
export default {
    props: ['dob'],
}
</script>