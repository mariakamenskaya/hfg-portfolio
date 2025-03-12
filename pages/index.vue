<template>
	<div class="container">
		<div class="left-section">
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
						<span v-if="showLastName" class="full-name"
							>amenskaya</span
						>
					</transition>
				</div>
			</div>
			<nav class="navigation">
				<NuxtLink to="/" class="nav-item active">Intro</NuxtLink>
				<NuxtLink to="/work" class="nav-item">Work</NuxtLink>
				<NuxtLink to="/about" class="nav-item">About</NuxtLink>
				<NuxtLink to="/contact" class="nav-item">Contact</NuxtLink>
			</nav>
		</div>
		<div class="right-section">
			<h1>
				Hello there, I'm a designer who cares about making beautiful
				things that help people.
			</h1>
		</div>
	</div>
</template>

<script lang="ts" setup>
import { ref } from "vue";
const showFullName = ref(false);
const showLastName = ref(false);
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

.left-section {
	flex: 1;
	display: flex;
	flex-direction: column;
	gap: 2rem;
}

.right-section {
	flex: 2;
	padding: 2rem;
	margin-top: 8rem;
}

.initials-container {
	position: absolute;
	top: 2rem;
	left: 0;
	right: 0;
	display: flex;
	justify-content: space-between;
	padding: 0 2rem;
	width: 100%;
}

.initial {
	display: flex;
	align-items: center;
	font-size: 4rem;
	font-weight: 400;
	cursor: pointer;
	position: relative;
}

.initial:last-child {
	margin-right: 15%;
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

.navigation {
	display: flex;
	flex-direction: column;
	gap: 1rem;
	margin-top: 8rem;
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

h1 {
	font-size: 3.5rem;
	font-weight: 400;
	line-height: 1.2;
	max-width: 800px;
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
