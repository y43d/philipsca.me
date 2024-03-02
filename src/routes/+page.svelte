<script>
	import { emailAddress, github } from '$lib/stores/contactInformation';
	import IconWrapper from '../lib/components/IconWrapper.svelte';
	import Icon from '@iconify/svelte';
	import Separator from '../lib/components/Separator.svelte';
	import lazyLoadVideos from '$lib/js/lazyLoadVideo.js';
	import Required from '../lib/components/Required.svelte';
	import NotificationManager from '/node_modules/svelte-legos/dist/actions/notifyAction/NotificationManager';

	let waitingForFormResponse = false;

	async function submitForm(e) {
		waitingForFormResponse = true;
		const formData = new FormData(e.target);
		const response = await fetch('https://api.staticforms.xyz/submit', {
			method: 'POST',
			body: new URLSearchParams(formData),
			headers: {
				'Content-Type': 'application/x-www-form-urlencoded'
			}
		});
		if (response.ok) {
			NotificationManager.getInstance().createNotification(
				'Success!',
				'Email sent! I will be back in contact with you soon.',
				'success',
				10000
			);
			e.target.reset();
		} else {
			NotificationManager.getInstance().createNotification(
				'Error!',
				'Email was not able to send! Please, use the email icon at the top & bottom of the page to manually email me & let me know this is not working.',
				'error',
				10000
			);
		}

		waitingForFormResponse = false;
	}
</script>

<svelte:head>
	<script type="text/javascript">
		var mountCaptcha = function () {
			setTimeout(() => {
				grecaptcha.render('captcha', {
					sitekey: '6Lfn-igpAAAAAP5CsKlZDPkbEJZguYKwlLRuWSSR',
					theme: 'dark'
				});
			}, 2000);
		};
	</script>

	<script
		src="http://www.google.com/recaptcha/api.js?onload=mountCaptcha&render=explicit"
		async
		defer
	></script>
</svelte:head>
<main class="container">
	<!-- INTRODUCTION    -->
	<div class="flex justify-center pb-5">
		<h1 class="animate-bounce m-0 text-5xl">👋🏽</h1>
		<h1 class="font-sans m-0 text-5xl">Hello!</h1>
	</div>
	<div class="flex flex-col items-center">
		<p class="m-0 text-2xl text-white">
			My name is <strong class="text-blue-200">Philip</strong>,
		</p>
		<p class="m-0 text-lg text-center">I'm a professional & flexible web site/app developer.</p>
	</div>

	<!-- SOCIAL LINKS -->
	<div class="flex gap-8 justify-center mt-10">
		<IconWrapper href={$github} tooltip="GitHub">
			<Icon icon="mdi:github" width="32" />
		</IconWrapper>
		<IconWrapper href="mailto:{$emailAddress}" tooltip="Email Me">
			<Icon icon="mdi:email" width="32" height="32" />
		</IconWrapper>
	</div>

	<Separator />

	<!-- ABOUT ME -->
	<div>
		<p class="text-2xl text-white text-center">A little about me...</p>
		<p>
			<span class="text-blue-300">Hello!</span> My name is <span class="underline">Philip</span>,
			and I enjoy creating things for the web. My interest spawned at the age of just 9 years old,
			where my own curiosity drove me learn HTML & CSS via whatever methods were available at the
			time. <br />
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
		<p class="text-2xl text-white">Here's a piece of my work...</p>

		<div class="flex align-middle items-center">
			<div>
				<p class="text-xl text-white text-center whitespace-nowrap mb-1">Cult of Intellect</p>
				<p class="text-center text-sm">
					<span class="text-white">Industry: </span>Software Developemnt
				</p>
				<hr />
				<p class="mt-5">
					<span class="text-blue-300">Simple</span> & <em class="text-purple-200">smooth</em>
					animations, with the <span class="text-blue-200">right</span> typography. This brings a
					sense of <span class="text-white">simplicity</span> using the
					<span class="text-purple-100">minified</span>
					approach I took with this website.
					<br /><br />
					I designed this site with usability in mind, and making sure the site was easy to navigate.
					<br /><br />
					Developing the website for Cult of Intellect was an inspiring project which taught me many
					things.
				</p>
				<a href="https://cultofintellect.com" role="button" class="w-full contrast" target="_blank"
					>Visit <Icon icon="mdi:open-in-new" class="inline" /></a
				>
			</div>
			<div use:lazyLoadVideos class="pl-2 hidden md:block">
				<!-- svelte-ignore a11y-media-has-caption -->
				<video class="video-3d transform-none" muted autoplay loop preload="none">
					<source src="/video/cultofintellect.mp4" type="video/mp4" />
				</video>
			</div>
		</div>
	</div>

	<Separator />

	<!-- NEED A WEBSITE? -->
	<div class="flex flex-col items-center" id="contact">
		<p class="text-2xl text-white mb-0">Get in touch.</p>
		<p class="text-center">
			Let me know your requirements for your upcoming application, this can range from a basic
			websites, to full-fledged applications.
		</p>

		<form class="w-full" on:submit|preventDefault={submitForm}>
			<input type="hidden" name="accessKey" value="fefd8491-63af-482e-852b-a2d954c09702" />
			<input type="text" name="honeypot" style="display: none;" />

			<div class="form-group">
				<label for="name">Full Name <Required /></label>
				<input type="text" id="name" name="name" placeholder="" required />
				<small>So I know who to address when responding!</small>
			</div>

			<div class="grid">
				<div class="form-group">
					<label for="email">Email Address <Required /></label>
					<input type="email" id="email" name="email" placeholder="example@example.com" required />
					<small>I'll get back to you at this email address.</small>
				</div>

				<div class="form-group">
					<label for="email">Phone No</label>
					<input type="text" id="phone" name="phone" placeholder="+44" />
					<small>Or, your phone number if you'd like me to return a call.</small>
				</div>
			</div>

			<div class="grid">
				<div class="form-group">
					<label for="$business_name">Business Name <small>(optional)</small></label>
					<input
						type="text"
						id="$business_name"
						name="$business_name"
						placeholder="Your Business Ltd"
					/>
				</div>

				<div class="form-group">
					<label for="$business_website">Business Website <small>(optional)</small></label>
					<input
						type="text"
						id="$business_website"
						name="$business_website"
						placeholder="example.com"
					/>
				</div>
			</div>

			<div class="form-group">
				<label for="email">Message <Required /></label>
				<textarea
					name="message"
					id="message"
					rows="10"
					placeholder="Let me know a bit about your business, and what you expect from your website or app. We can take it from there."
					required
				></textarea>
			</div>

			<!-- <div id="captcha" class="g-recaptcha flex justify-center mb-5"></div> -->

			<button aria-busy={waitingForFormResponse ? 'true' : 'false'} type="submit"
				>{waitingForFormResponse ? 'Sending...' : 'Send!'}</button
			>
		</form>
	</div>
</main>

<style>
	.video-3d {
		border-radius: 4%;
		border: 1px white solid;
		transform: rotate3d(0, 1, 0.2, 32deg);
	}
</style>
