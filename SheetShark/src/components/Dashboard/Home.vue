<script setup>
import { ref, onMounted } from "vue"
import axios from "axios"

const jobData = ref([])

onMounted(async () => {
	try {
		//const { data } = await axios.get("http://localhost:8000/api/two-item.php")
		const { data } = await axios.get("https://bb7c-99-52-252-157.ngrok-free.app/api/two-item.php", {
			headers: {
				"ngrok-skip-browser-warning": "true",
			},
		})
		console.log(data)
		jobData.value = data.data
		console.log(jobData.value)
	} catch (err) {
		console.error(err)
	}
})
</script>

<template>
	<div class="flex flex-row w-screen justify-center gap-4">
		<div class="basis-sm border border-white border-solid rounded-sm py-6 px-4">
			<h3 class="text-white mb-2 text-xl">Job Openings:</h3>
			<p class="text-white">Department 1: {{ jobData[0]?.value1 }}</p>
			<p class="text-white">Department 2: {{ jobData[0]?.value2 }}</p>
		</div>
		<div class="basis-sm border border-white border-solid rounded-sm py-6 px-4">
			<h3 class="text-white mb-2 text-xl">Grade:</h3>
			<p class="text-white">Department 1: {{ jobData[1]?.value1 }}</p>
			<p class="text-white">Department 2: {{ jobData[1]?.value2 }}</p>
		</div>
		<div class="basis-sm border border-white border-solid rounded-sm p-4">
			<h3 class="text-white mb-2 text-xl">Test</h3>
		</div>
	</div>
</template>
