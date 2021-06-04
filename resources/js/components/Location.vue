<template>
    <address>
        <div>{{ location.street.number + ' ' + location.street.name }}</div>
        <div>{{ location.city + ', ' + location.state + ', ' + location.country + ' ' + location.postcode }}</div>
    </address>
</template>

<script>
export default {
    props: ['location'],
}
</script>