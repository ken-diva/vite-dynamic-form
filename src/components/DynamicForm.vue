<script setup lang="ts">
import { ref } from "vue";

let id = 0;

const todoBaru = ref("");
const dataTodo = ref([{ id: id++, text: "" }]);

function tambahTodo() {
	dataTodo.value.push({ id: id++, text: todoBaru.value });
	todoBaru.value = "";
}

function hapusTodo(todo) {
	dataTodo.value = dataTodo.value.filter((t) => t !== todo);
}
</script>

<template>
	<!-- loop form -->
	<div v-for="(todo, index) in dataTodo">
		<input v-model="todo.text" @keyup.enter="tambahTodo" :key="index" />
	</div>
	<br />
	<button @click="tambahTodo">Tambah Todo</button>

	<ul>
		<!-- loop hasil input todos -->
		<li v-for="todo in dataTodo" :key="todo.id">
			{{ todo.text }} <button @click="hapusTodo(todo)">X</button>
		</li>
	</ul>
</template>
