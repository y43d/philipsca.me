<script>
	export let href;
	export let tooltip;
	export let tooltip_direction;
</script>

<a
	{href}
	target="_blank"
	class="text-white transition-transform hover:-translate-y-1"
	data-tooltip={tooltip}
	data-placement={tooltip_direction}
>
	<slot />
</a>
