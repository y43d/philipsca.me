<script>
	import { emailAddress, linkedIn, github } from '$lib/stores/contactInformation';
	import Icon from '@iconify/svelte';
	import IconWrapper from '../lib/components/IconWrapper.svelte';
	import Separator from '../lib/components/Separator.svelte';
</script>

<main class="container">
	<!-- INTRODUCTION    -->
	<div class="flex justify-center pb-5">
		<h1 class="animate-bounce m-0 text-5xl">👋🏽</h1>
		<h1 class="font-sans m-0 text-5xl">Hey.</h1>
	</div>
	<div class="flex flex-col items-center">
		<p class="m-0 text-2xl text-white">
			My name's <strong class="text-blue-200">Philip</strong>.
		</p>
		<p class="m-0 text-lg">And I create applications for the web.</p>
	</div>

	<!-- SOCIAL LINKS -->
	<div class="flex gap-8 justify-center mt-10">
		<IconWrapper href={$github} tooltip="GitHub">
			<Icon icon="mdi:github" width="32" />
		</IconWrapper>
		<IconWrapper href="mailto:{$emailAddress}" tooltip="Get in touch">
			<Icon icon="mdi:email" width="32" height="32" />
		</IconWrapper>
	</div>

	<Separator />

	<!-- ABOUT ME -->
	<div class="flex flex-col">
		<p class="text-2xl text-white text-center">A little about me...</p>
		<p>
			Hello! My name is Philip, and I enjoy creating things for the web. My interest spawned at the
			age of just 9 years old, where my own curiosity & interest drove me learn HTML & CSS via
			whatever methods were available at the time. <br />
			At the same age, through online courses & YouTube tutorials, I created my first public-facing website.
		</p>
		<p>
			Fast forward to today. I've been professionally developing & customizing various applications.
		</p>
		<p>Here are a few technologies which i've been using recently.</p>
		<div class="flex gap-7 flex-wrap">
			<IconWrapper tooltip="PHP" tooltip_direction="bottom">
				<Icon icon="logos:php" width="32" height="32" />
			</IconWrapper>
			<IconWrapper tooltip="Javascript (ES6+)" tooltip_direction="bottom">
				<Icon class="text-black" icon="logos:javascript" width="32" height="32" />
			</IconWrapper>
			<IconWrapper tooltip="Svelte/SvelteKit" tooltip_direction="bottom">
				<Icon icon="logos:svelte-icon" width="32" height="32" />
			</IconWrapper>
			<IconWrapper tooltip="TailwindCSS" tooltip_direction="bottom"
				><Icon icon="logos:tailwindcss-icon" width="32" height="32" />
			</IconWrapper>
			<IconWrapper tooltip="Node.js" tooltip_direction="bottom">
				<Icon icon="vscode-icons:file-type-node" width="32" height="32" />
			</IconWrapper>
			<IconWrapper tooltip="PrestaShop" tooltip_direction="bottom">
				<Icon icon="logos:prestashop" width="32" height="32" />
			</IconWrapper>
			<IconWrapper tooltip="Wordpress" tooltip_direction="bottom">
				<Icon icon="skill-icons:wordpress" width="32" height="32" />
			</IconWrapper>
			<IconWrapper tooltip="Bootstrap" tooltip_direction="bottom">
				<Icon icon="logos:bootstrap" width="32" height="32" />
			</IconWrapper>
		</div>
	</div>

	<Separator />

	<!-- MY WORK -->
	<div class="flex flex-col items-center" id="projects">
		<p class="text-2xl text-white">And here's a piece of my work...</p>

		<article class="text-center">
			<header>Cult of Intellect Website</header>
			<img src="" />
			<footer>With design</footer>
		</article>
	</div>

	<!-- NEED A WEBSITE? -->
</main>
