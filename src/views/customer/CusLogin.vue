<template>
    <div class="
		min-h-screen
		flex
		items-center
		justify-center
		py-12
		px-4
		sm:px-6
		lg:px-8
	">
		<div class="max-w-md w-full text-center">

			<h2 class="mb-8 text-4xl font-extrabold text-gray-900">
				Log In
			</h2>

			<form @submit.prevent="cusLogin" class="mb-3" action="#">
				<div class="rounded-md shadow-sm">
					<input
                        v-model="cusLoginData.email"
                        type="email" 
                        name="email" 
                        autocomplete="email" 
                        class="
                            appearance-none
                            relative
                            block
                            w-full
                            px-3
                            py-2
                            placeholder-gray-500
                            text-gray-900
                            rounded-md
                            focus:outline-none
                            focus:z-10
                        " 
                        placeholder="Email address" 
                    />
				</div>

				<div class="mt-2 rounded-md shadow-sm">
					<input 
                        v-model="cusLoginData.password"
                        type="password" 
                        name="password" 
                        autocomplete="password" 
                        class="
                            appearance-none
                            relative
                            block
                            w-full
                            px-3
                            py-2
                            placeholder-gray-500
                            text-gray-900
                            rounded-md
                            focus:outline-none
                            focus:z-10
                            
                        " 
                        placeholder="Password" 
                    />
				</div>

				<button type="submit" class="
					mt-4
					group
					relative
					w-full
					flex
					justify-center
					py-2
					px-4
					border border-transparent
					text-lg
					rounded-md
					text-black
					bg-blue-400
					hover:bg-blue-500
					focus:outline-none
                    font-black
				">
					Sign in
				</button>

			</form>

			<p class="mt-8">
				Don't have an account?
                <router-link to="/register" class="font-medium text-blue-600 hover:text-blue-500">
                    Sign up
                </router-link>
			</p>
		</div>
	</div>
</template>

<script>
import { mapState, mapActions } from 'vuex'

export default {
    name:'CusLogin',
    data() {
        return {
            cusLoginData:{
                email: '',
                password:''
            }
        }
    },
    computed:{
        ...mapState(['isLogin'])
    },
    methods: {
        ...mapActions(['loginAction']),
        async cusLogin() {
            await this.loginAction(
                {
                data: this.cusLoginData,
                addRoute: ''
            })
            if (this.isLogin) {
                for (const key in this.cusLoginData) {
                    this.cusLoginData[key] = ''
                }
                this.$router.push({ name: 'CusHome' })
            }
        }
    }
}
</script>

<style>

</style>