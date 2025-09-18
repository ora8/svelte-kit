<script lang="ts">
	import { onMount } from 'svelte';

	export let width: number = 400;
	export let height: number = 300;
	export let color: string = '#000';
	export let background: string = '#fff';

	let canvas: HTMLCanvasElement;
	let context: CanvasRenderingContext2D;
	let isDrawing = false;
	let start = { x: 0, y: 0 };

	onMount(() => {
		// ✅ canvas will definitely be defined here
		if (!canvas) {
			console.error('Canvas is undefined!');
			return;
		}

		const ctx = canvas.getContext('2d');
		if (!ctx) {
			console.error('Canvas context could not be initialized!');
			return;
		}

		context = ctx;
		context.lineWidth = 2;
		context.strokeStyle = color;

		// Optional: Fill background
		context.fillStyle = background;
		context.fillRect(0, 0, width, height);
	});

	// reactive stroke color update
	$: if (context) {
		context.strokeStyle = color;
	}

	function handleStart(e: PointerEvent) {
		if (!context) return;
		isDrawing = true;
		start = { x: e.offsetX, y: e.offsetY };
	}

	function handleMove(e: PointerEvent) {
		if (!context || !isDrawing) return;
		context.beginPath();
		context.moveTo(start.x, start.y);
		context.lineTo(e.offsetX, e.offsetY);
		context.stroke();
		start = { x: e.offsetX, y: e.offsetY };
	}

	function handleEnd() {
		isDrawing = false;
	}
</script>

<canvas
	bind:this={canvas}
	width={width}
	height={height}
	style="border: 1px solid #ccc; background: {background}; touch-action: none;"
	on:pointerdown={handleStart}
	on:pointermove={handleMove}
	on:pointerup={handleEnd}
	on:pointerleave={handleEnd}
/>
