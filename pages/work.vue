<template>
	<div class="container">
		<div class="initials-container" :class="{ hidden: isNavigationHidden }">
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
		<div class="left-section" :class="{ hidden: isNavigationHidden }">
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
import { ref, onMounted, onUnmounted } from "vue";

const showFullName = ref(false);
const showLastName = ref(false);
const isNavigationHidden = ref(false);

const handleScroll = () => {
	const scrollPosition = window.scrollY;
	isNavigationHidden.value = scrollPosition > 100;
};

onMounted(() => {
	window.addEventListener("scroll", handleScroll);
});

onUnmounted(() => {
	window.removeEventListener("scroll", handleScroll);
});

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
	transition: transform 0.5s ease;
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
	transition: transform 0.5s ease;
}

.left-section.hidden {
	transform: translateX(-100%);
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
	padding-left: 9rem;
	margin-top: 8rem;
	overflow-y: auto;
	height: 100vh;
}

.projects-container {
	display: flex;
	flex-direction: column;
	width: 100%;
}

.project-card {
	text-decoration: none;
	color: inherit;
	width: 100%;
	margin-bottom: -6rem;
	padding-bottom: 8rem;
}

.project-image {
	width: 100%;
	height: 75vh;
	background-color: #e5e5e5;
	border-radius: 8px;
}

.project-title {
	font-size: 1rem;
	font-weight: 400;
	color: #666;
	margin-top: 1rem;
	padding-left: 0.5rem;
}

.fade-enter-active,
.fade-leave-active {
	transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
	opacity: 0;
}
</style>
