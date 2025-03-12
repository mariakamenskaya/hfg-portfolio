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
			<button class="back-button" @click="$router.push('/work')">
				← Back to Work
			</button>
			<div v-if="project" class="project-content">
				<h1>{{ project.title }}</h1>
				<div class="project-details">
					<div class="project-image"></div>
					<p class="project-description">{{ project.description }}</p>
				</div>
			</div>
		</div>
	</div>
</template>

<script lang="ts" setup>
import { ref } from "vue";

const showFullName = ref(false);
const showLastName = ref(false);

const route = useRoute();
const projectId = route.params.id as string;

const projects = {
	"nass-clean": {
		title: "Nass-clean water, clean data",
		description:
			"A project focused on water quality monitoring and data visualization.",
	},
	calmee: {
		title: "Calmee: your little helper",
		description: "An app designed to help users manage stress and anxiety.",
	},
	"project-3": {
		title: "Project 3",
		description: "Description for Project 3.",
	},
	"project-4": {
		title: "Project 4",
		description: "Description for Project 4.",
	},
};

const project = projects[projectId as keyof typeof projects];
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
}

.back-button {
	background: none;
	border: none;
	font-size: 1.1rem;
	color: #666;
	cursor: pointer;
	padding: 0;
	margin-bottom: 2rem;
	transition: color 0.3s ease;
}

.back-button:hover {
	color: #000;
}

.project-content {
	max-width: 800px;
}

h1 {
	font-size: 2rem;
	font-weight: 400;
	margin-bottom: 2rem;
}

.project-details {
	display: flex;
	flex-direction: column;
	gap: 2rem;
}

.project-image {
	width: 100%;
	height: 500px;
	background-color: #e5e5e5;
	border-radius: 4px;
}

.project-description {
	font-size: 1.1rem;
	line-height: 1.6;
	color: #333;
}
</style>
