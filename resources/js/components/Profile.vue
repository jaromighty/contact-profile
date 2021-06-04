<template>
    <div v-if="user" class="px-4 py-6">
        <div class="flex items-center">
            <div class="">
                <img class="h-16 w-16 rounded-full" :src="user.picture.thumbnail" alt="" />
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                user: null,
            }
        },
        mounted() {
            axios.get('https://randomuser.me/api')
                .then(response => (this.user = response.data.results[0]));
        }
    }
</script>
