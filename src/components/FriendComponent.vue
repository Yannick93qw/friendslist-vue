<script>
	export default {
	props: ["name", "email", "phone", "id", "image"],
	data() {
		return {
			visible: false
		}
	},
	methods: {
		toggleShow() {
			this.visible = !this.visible
		},
		emitDelete() {
			this.$emit("delete", this.id)
		}
	}
}
</script>

<template>
<h2>{{name}}</h2>
<h2>{{image}}</h2>
<button @click="this.toggleShow">Show Details</button>
<button @click="this.emitDelete">Delete</button>
<ul v-show="this.visible">
	<li><strong>Phone:</strong>{{phone}}</li>
	<li><strong>Email:</strong> {{email}}</li>
</ul>
</template>