<!-- App.vue -->
<template>
	<div>
	  <div v-for="(item, index) in data" :key="index" @dblclick="selectItem(item)">
		<p class="text-primary fs-3">{{ item.name }}: {{ item.value }}</p>
	  </div>
	  <hr />
	  <EditItem v-if="selectedItem" :item="selectedItem" @update="updateItem" />
	</div>
  </template>
  
  <script lang="ts">
  import { defineComponent } from 'vue';
  import EditItem from './EditItem.vue';
  import 'bootstrap/dist/css/bootstrap.css';

  interface Item {
	name: string;
	value: string;
  }
  
  export default defineComponent({
	components: {
	  EditItem,
	},
	data() {
	  return {
		data: [
		  {
			name: 'foo1',
			value: 'bar1',
		  },
		  {
			name: 'foo2',
			value: 'bar2',
		  },
		] as Item[],
		selectedItem: null as Item | null,
	  };
	},
	methods: {
	  selectItem(item: Item) {
		this.selectedItem = item;
	  },
	  updateItem(newValue: string) {
		if (this.selectedItem) {
		  this.selectedItem.value = newValue;
		  this.selectedItem = null;
		}
	  },
	},
  });
  </script>
  