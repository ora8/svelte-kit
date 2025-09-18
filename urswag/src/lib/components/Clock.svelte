<script lang="ts">
	import { onMount } from 'svelte';

	export let size: number = 400;
	export let color: string = '#000';
	export let background: string = '#fff';

	let canvas: HTMLCanvasElement | undefined;
	let context: CanvasRenderingContext2D;
	let secondandAngle: number;
    let minuteAngle: number;
    let hourAngle: number;
    let interval = 50;

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

        initClock(context);

		context.fillStyle = background;
		context.fillRect(0, 0, size, size);
		drawClock(context);
	});

	// reactive stroke color update
	$: if (context) {
		context.strokeStyle = color;
	}

    function initClock(context: CanvasRenderingContext2D) {
        const now = new Date();
        const seconds = now.getSeconds();
        const minutes = now.getMinutes();
        const hours = now.getHours() % 12;

        secondandAngle = (seconds / 60) * 2 * Math.PI - Math.PI / 2;
        minuteAngle = (minutes / 60) * 2 * Math.PI - Math.PI / 2;
        hourAngle = (hours / 12) * 2 * Math.PI - Math.PI / 2 + (minutes / 60) * (2 * Math.PI / 12);
        setInterval(() => {
            updateClock(context);
        }, interval);
    }   

    function drawClock(context: CanvasRenderingContext2D) {
		context.lineWidth = 2;
		context.strokeStyle = color;
		let l1 = size / 2;
		let l2 = l1 - 5;
        let mid = size / 2;
        // Draw clock circle
		for (let i = 0; i < 60; i++) {
			let angle = (i / 60) * 2 * Math.PI;
			let x1 = mid + l1 * Math.cos(angle);
			let y1 = mid + l1 * Math.sin(angle);
			let x2 = mid + l2 * Math.cos(angle);
			let y2 = mid + l2 * Math.sin(angle);
			context.beginPath();
			context.moveTo(x1, y1);
			context.lineTo(x2, y2);
			context.stroke();
		}

        context.lineWidth = 6;
        l1 = size / 2 - 3;
        l2 = l1 - 40;
        for (let i = 0; i < 12; i++) {
            let angle = (i / 12) * 2 * Math.PI;
            let x1 = mid + l1 * Math.cos(angle);
            let y1 = mid + l1 * Math.sin(angle);
            let x2 = mid + l2 * Math.cos(angle);
            let y2 = mid + l2 * Math.sin(angle);
            context.beginPath();
            context.moveTo(x1, y1);
            context.lineTo(x2, y2);
            context.stroke();
        }

        // Draw text
        context.font = "24px Arial";
        context.textAlign = "center";
        context.textBaseline = "middle";
        context.fillStyle = color;
        context.fillText("urswag", mid, 100);
        context.font = "12px Arial";
        context.fillText("AUTOMATIC", mid, 124);

        context.strokeRect(mid + 118, mid - 32, 80, 56);
        let currentDate = new Date();
        const day: number = currentDate.getDate();
        context.font = "48px Arial";
        context.textAlign = "right";
        context.fillText(day.toString(), size - 60, mid);

        drawSwissFlag(context);
 	}

    function updateClock(context: CanvasRenderingContext2D) {
        context.clearRect(0, 0, size, size);
        context.fillStyle = background;
        context.fillRect(0, 0, size, size);
        drawClock(context);

        let mid = size / 2;
        // Draw hour hand
        context.lineWidth = 8;
        context.beginPath();
        context.lineTo(mid - 40 * Math.cos(hourAngle), mid - 40 * Math.sin(hourAngle));
        context.lineTo(mid + (mid - 100) * Math.cos(hourAngle), mid + (mid - 100) * Math.sin(hourAngle));
        context.stroke();

        // Draw minute hand
        context.lineWidth = 6;
        context.beginPath();
        context.lineTo(mid - 40 * Math.cos(minuteAngle), mid - 40 * Math.sin(minuteAngle));
        context.lineTo(mid + (mid - 60) * Math.cos(minuteAngle), mid + (mid - 60) * Math.sin(minuteAngle));
        context.stroke();

        // Draw second hand
        context.lineWidth = 2;
        context.beginPath();
        context.lineTo(mid - 80 * Math.cos(secondandAngle), mid - 80 * Math.sin(secondandAngle));
        context.lineTo(mid + (mid - 40) * Math.cos(secondandAngle), mid + (mid - 40) * Math.sin(secondandAngle));
        context.stroke();

        // Update angles
        secondandAngle += (Math.PI / 30) * (interval / 1000); // every 50ms
        minuteAngle += (Math.PI / 1800) *  (interval / 1000); // every 50ms
        hourAngle += (Math.PI / 21600) * s (interval / 1000); // every 50ms
    }

    function drawSwissFlag(context: CanvasRenderingContext2D) {
 
    const flagWidth = 120; // Width of the flag
    const flagHeight = 90; // Height of the flag
    const x = size / 2 - flagWidth / 2;
    const y = size - 140 - flagHeight / 2;

    // Draw the red background
    context.fillStyle = 'red';
    context.fillRect(x, y, flagWidth, flagHeight);

    // Draw the white cross
    const crossWidth = 20; // Width of the cross
    const crossHeight = 70; // Height of the vertical part of the cross

    // Vertical part of the cross
    context.fillStyle = 'white';
    context.fillRect(x + (flagWidth / 2) - (crossWidth / 2), y + (flagHeight / 2) - (crossHeight / 2), crossWidth, crossHeight);
    
    // Horizontal part of the cross
    context.fillRect(x + (flagWidth / 2) - (crossHeight / 2), y + (flagHeight / 2) - (crossWidth / 2), crossHeight, crossWidth);
  }
</script>

<canvas
	bind:this={canvas}
	width={size}
	height={size}
	style="border: 1px solid #ccc; background: {background}; touch-action: none;"
/>
