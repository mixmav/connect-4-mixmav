<template>
	<div id="projects-app-connect-4-container"></div>
	<Head title="Connect 4" />
</template>

<script>
import { createApp } from 'vue'

import { store } from './store/store';
import App from './App.vue';
import mitt from 'mitt';
import { Link, Head } from '@inertiajs/inertia-vue3';
import Base from '@/Pages/Layout/Base.vue';

export default {
	components: {
		Head,
	},
	mounted(){
		const emitter = mitt();
		this.app = createApp(App).use(store);
		
		this.app.config.globalProperties.emitter = emitter;
		this.app.component('Link', Link);
		this.app.mount('#projects-app-connect-4-container')
	},
	unmounted(){
		this.app.unmount();
	},

	data(){
		return {
			app: {},
		}
	},
	layout: Base,
}

</script>