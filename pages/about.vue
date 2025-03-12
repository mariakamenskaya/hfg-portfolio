<template>
	<div class="container">
		<div class="background-image"></div>
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
				<NuxtLink to="/" class="nav-item">Intro</NuxtLink>
				<NuxtLink to="/work" class="nav-item">Work</NuxtLink>
				<NuxtLink to="/about" class="nav-item active">About</NuxtLink>
				<NuxtLink to="/contact" class="nav-item">Contact</NuxtLink>
			</nav>
		</div>
		<div class="right-section">
			<div class="content">
				<h1>Hello, my name is Maria.</h1>
				<div class="text-content">
					<p>
						I'm studying Interaction Design in my 4th semester at
						the Schwäbisch Gmünd University of Applied Sciences. For
						me, design means more than just aesthetics - it's a way
						of making the world a better place to live. Be it
						through visual design that inspires or through well
						thought-out interactions that make everyday life easier.
						My goal is to create experiences that are both
						functional and emotionally enriching.
					</p>
					<p>
						Away from design, you can often find me in music -
						whether listening, discovering or making. I also enjoy
						embroidery and on holiday I like to try out new water
						sports - from stand-up paddling to anything that sounds
						like adventure.
					</p>
				</div>
			</div>
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

.background-image {
	position: fixed;
	top: 0;
	left: 0;
	width: 33.33vw;
	height: 100vh;
	background-image: url("/images/profile.jpg");
	background-size: cover;
	background-position: center;
	opacity: 1;
	z-index: -1;
}

.left-section {
	flex: 1;
	display: flex;
	flex-direction: column;
	gap: 2rem;
	position: relative;
	z-index: 1;
}

.right-section {
	flex: 2;
	padding: 2rem;
	padding-left: 10rem;
	margin-top: 8rem;
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
	text-shadow: 0 0 10px white;
}

.nav-item:hover {
	color: #000;
}

.nav-item.active {
	color: #000;
}

h1 {
	font-size: 2rem;
	font-weight: 400;
	line-height: 1.2;
	margin-bottom: 2rem;
}

.text-content {
	max-width: 800px;
}

.text-content p {
	font-size: 1.1rem;
	line-height: 1.6;
	margin-bottom: 2rem;
	color: #333;
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
