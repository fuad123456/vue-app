<!-- EditItem.vue -->
<template>
	<div>
	  <h3>Edit item:</h3>
	  <form @submit.prevent="updateItem" class="">
		<label class="mb-2">
		  Value:
		  <input v-model="newValue" class="form-control form-control-lg" type="text" />
		</label>
		<div class="px-2">
			<button type="submit" class="btn btn-success me-2">Save</button>
			<button @click="cancelEdit" class="btn btn-danger">Cancel</button>
		</div>
	  </form>
	</div>
  </template>
  
  <script lang="ts">
  import { defineComponent } from 'vue';
  import 'bootstrap/dist/css/bootstrap.css';

  interface Item {
	name: string;
	value: string;
  }
  
  export default defineComponent({
	props: {
	  item: {
		type: Object as () => Item,
		required: true,
	  },
	},
	data() {
	  return {
		newValue: this.item.value,
	  };
	},
	methods: {
	  updateItem() {
		this.$emit('update', this.newValue);
	  },
	  cancelEdit() {
		this.$emit('update', this.item.value);
	  },
	},
  });
  </script>
  