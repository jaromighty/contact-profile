<template>
    <div v-if="user" class="p-6">
        <div class="flex items-center space-x-8">
            <div class="">
                <img class="h-40 w-40 rounded-full" :src="user.picture.large" alt="" />
            </div>
            <div class="grid grid-cols-2 grid-rows-3 gap-8">
                <svg @click="changeActive('bio')" class="w-10 h-10 text-blue-600 cursor-pointer hover:text-blue-700" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5.121 17.804A13.937 13.937 0 0112 16c2.5 0 4.847.655 6.879 1.804M15 10a3 3 0 11-6 0 3 3 0 016 0zm6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                <svg @click="changeActive('location')" class="w-10 h-10 text-blue-600 cursor-pointer hover:text-blue-700" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"></path><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z"></path></svg>
                <svg @click="changeActive('email')" class="w-10 h-10 text-blue-600 cursor-pointer hover:text-blue-700" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"></path></svg>
                <svg @click="changeActive('phone')" class="w-10 h-10 text-blue-600 cursor-pointer hover:text-blue-700" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"></path></svg>
                <svg @click="changeActive('birthday')" class="w-10 h-10 text-blue-600 cursor-pointer hover:text-blue-700" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 15.546c-.523 0-1.046.151-1.5.454a2.704 2.704 0 01-3 0 2.704 2.704 0 00-3 0 2.704 2.704 0 01-3 0 2.704 2.704 0 00-3 0 2.704 2.704 0 01-3 0 2.701 2.701 0 00-1.5-.454M9 6v2m3-2v2m3-2v2M9 3h.01M12 3h.01M15 3h.01M21 21v-7a2 2 0 00-2-2H5a2 2 0 00-2 2v7h18zm-3-9v-2a2 2 0 00-2-2H8a2 2 0 00-2 2v2h12z"></path></svg>
                <svg @click="changeActive('security')" class="w-10 h-10 text-blue-600 cursor-pointer hover:text-blue-700" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 15v2m-6 4h12a2 2 0 002-2v-6a2 2 0 00-2-2H6a2 2 0 00-2 2v6a2 2 0 002 2zm10-10V7a4 4 0 00-8 0v4h8z"></path></svg>
            </div>
        </div>
        <div class="mt-10">
            <h1 class="text-2xl font-bold leading-7 text-gray-900">{{user.name.first + ' ' + user.name.last}}</h1>
            <div class="mt-6">
                <bio v-if="active === 'bio'" />
                <location v-if="active === 'location'" :location="user.location" />
                <email v-if="active === 'email'" :email="user.email" />
                <phone v-if="active === 'phone'" :phone="user.phone" :cell="user.cell" />
                <birthday v-if="active === 'birthday'" :dob="user.dob" />
                <security v-if="active === 'security'" :username="user.login.username" />
            </div>
        </div>
    </div>
</template>

<script>
    import Bio from "./Bio";
    import Location from "./Location";
    import Email from "./Email";
    import Phone from "./Phone";
    import Birthday from "./Birthday";
    import Security from "./Security";
    export default {
        components: {
            Bio,
            Location,
            Email,
            Phone,
            Birthday,
            Security,
        },
        data() {
            return {
                user: null,
                active: "bio"
            }
        },
        methods: {
            changeActive(active) {
                this.active = active;
            }
        },
        mounted() {
            axios.get('https://randomuser.me/api')
                .then(response => (this.user = response.data.results[0]));
        }
    }
</script>
