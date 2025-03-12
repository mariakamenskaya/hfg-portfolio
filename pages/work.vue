<template>
	<div class="container">
		<div class="initials-container">
			<div
				class="initial"
				@mouseover="showFullName = true"
				@mouseleave="showFullName = false"
			>
				<span class="letter">M</span>
				<transition name="fade">
					<span v-if="showFullName" class="full-name">aria</span>
				</transition>
			</div>
			<div
				class="initial"
				@mouseover="showLastName = true"
				@mouseleave="showLastName = false"
			>
				<span class="letter">K</span>
				<transition name="fade">
					<span v-if="showLastName" class="full-name">amenskaya</span>
				</transition>
			</div>
		</div>
		<div class="left-section">
			<nav class="navigation">
				<NuxtLink to="/" class="nav-item">Intro</NuxtLink>
				<NuxtLink to="/work" class="nav-item active">Work</NuxtLink>
				<NuxtLink to="/about" class="nav-item">About</NuxtLink>
				<NuxtLink to="/contact" class="nav-item">Contact</NuxtLink>
			</nav>
		</div>
		<div class="right-section">
			<div class="projects-container">
				<NuxtLink
					v-for="project in projects"
					:key="project.id"
					:to="`/work/${project.id}`"
					class="project-card"
				>
					<div class="project-image"></div>
					<h3 class="project-title">{{ project.title }}</h3>
				</NuxtLink>
			</div>
		</div>
	</div>
</template>

<script lang="ts" setup>
import { ref } from "vue";

const showFullName = ref(false);
const showLastName = ref(false);

const projects = [
	{ id: "nass-clean", title: "Nass-clean water, clean data" },
	{ id: "calmee", title: "Calmee: your little helper" },
	{ id: "project-3", title: "Project 3" },
	{ id: "project-4", title: "Project 4" },
];
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400&display=swap");

* {
	font-family: "Inter", sans-serif;
}

.container {
	display: flex;
	min-height: 100vh;
	padding: 2rem;
	position: relative;
}

.initials-container {
	position: fixed;
	top: 2rem;
	left: 0;
	right: 0;
	display: flex;
	gap: 27.5rem;
	justify-content: flex-start;
	padding: 0 2rem;
	width: 100%;
	z-index: 10;
}

.initial {
	display: flex;
	align-items: center;
	font-size: 4rem;
	font-weight: 400;
	cursor: pointer;
	position: relative;
}

.letter {
	display: inline-block;
}

.full-name {
	display: inline-block;
	font-weight: 400;
	font-size: 4rem;
	position: absolute;
	left: 100%;
	white-space: nowrap;
}

.left-section {
	flex: 1;
	display: flex;
	flex-direction: column;
	gap: 2rem;
}

.navigation {
	display: flex;
	flex-direction: column;
	gap: 1rem;
	margin-top: 10.5rem;
	margin-left: 0.37rem;
	position: relative;
	z-index: 1;
}

.nav-item {
	text-decoration: none;
	color: #666;
	font-size: 1.2rem;
	transition: color 0.3s ease;
}

.nav-item:hover {
	color: #000;
}

.nav-item.active {
	color: #000;
}

.right-section {
	flex: 2;
	padding: 2rem;
	padding-left: 10rem;
	margin-top: 8rem;
	overflow-x: hidden;
}

.projects-container {
	display: flex;
	gap: 2rem;
	overflow-x: auto;
	padding-bottom: 2rem;
	-ms-overflow-style: none;
	scrollbar-width: none;
}

.projects-container::-webkit-scrollbar {
	display: none;
}

.project-card {
	flex: 0 0 auto;
	width: 400px;
	text-decoration: none;
	color: inherit;
	transition: transform 0.3s ease;
}

.project-card:hover {
	transform: translateY(-5px);
}

.project-image {
	width: 100%;
	height: 400px;
	background-color: #e5e5e5;
	margin-bottom: 1rem;
	border-radius: 4px;
}

.project-title {
	font-size: 1.1rem;
	font-weight: 400;
	color: #333;
}
</style>
