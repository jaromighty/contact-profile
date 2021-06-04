<template>
    <div class="border-t border-gray-300 pt-4 mt-4">
        <h2 class="text-xl font-bold leading-7 text-gray-900">Contact Me</h2>
        <form @submit.prevent="submitMessage">
            <div class="mt-2">
                <label for="name" class="block text-sm font-medium text-gray-700">Name</label>
                <input type="text" v-model="form.name" id="name" autocomplete="name" required class="mt-1 focus:ring-blue-500 focus:border-blue-500 block w-full shadow-sm sm:text-sm border-gray-300 rounded-md" />
            </div>
            <div class="mt-2">
                <label for="email" class="block text-sm font-medium text-gray-700">Email</label>
                <input type="email" v-model="form.email" id="email" autocomplete="email" required class="mt-1 focus:ring-blue-500 focus:border-blue-500 block w-full shadow-sm sm:text-sm border-gray-300 rounded-md" />
            </div>
            <div class="mt-2">
                <label for="message" class="block text-sm font-medium text-gray-700">About</label>
                <div class="mt-1">
                    <textarea id="message" v-model="form.message" rows="4" required class="shadow-sm focus:ring-blue-500 focus:border-blue-500 mt-1 block w-full sm:text-sm border-gray-300 rounded-md" />
                </div>
            </div>
            <div class="mt-4">
                <button type="submit" class="inline-flex justify-center py-2 px-4 border border-transparent shadow-sm text-sm font-medium rounded-md text-white bg-blue-600 hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-offset-2 bluefocus:ring-blue-500">
                    Send
                </button>
            </div>
        </form>
    </div>
</template>

<script>
export default {
    data() {
        return {
            name: null,
            email: null,
            message: null,
        }
    },
    methods: {
        submitMessage() {
            axios.post(this.form)
                .then(response => console.log(response));
        }
    }
}
</script>