<template>
    <div class="space-y-4">
        <p>Phone: {{ phone }}</p>
        <p>Cell: {{ cell }}</p>
    </div>
</template>

<script>
export default {
    props: ['phone', 'cell'],
}
</script>