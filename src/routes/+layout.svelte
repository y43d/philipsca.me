<script>
	import '../app.css';
	import '@picocss/pico/css/pico.css';
	import { emailAddress } from '$lib/stores/contactInformation';
	import IconWrapper from '../lib/components/IconWrapper.svelte';
	import Icon from '@iconify/svelte';
</script>

<html data-theme="dark" class="dark" lang="en">
	<body>
		<nav class="mx-10">
			<ul>
				<li class="uppercase">
					<a href="/"><strong class="text-blue-400">PhilipSCA</strong></a>
				</li>
				<li></li>
			</ul>
			<ul>
				<li><a href="#projects" class="text-blue-200 hover:text-blue-400">Projects</a></li>
				<li>
					<a href="#contact" class="text-blue-200 hover:text-blue-400">Contact</a>
				</li>
			</ul>
		</nav>

		<hr />

		<slot />

		<footer class="w-100 bottom-0 p-0">
			<hr />
			<div class="flex justify-between p-2">
				<p class="text-white m-0">Copyright © PhilipSCA 2024</p>
				<p class="text-white m-0">
					<IconWrapper href="mailto:{$emailAddress}" tooltip="Email Me" tooltip_direction="left">
						<Icon icon="mdi:email" width="32" height="32" />
					</IconWrapper>
				</p>
			</div>
		</footer>
	</body>
</html>
