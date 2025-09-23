<script>
 	import video from '$lib/assets/movies/dimm.mp4';
</script>

<section class="main-section">
<div class="arduino-container">
<div>
<h1>Arduino Uno R4</h1>
   <p>
    The Arduino Uno R4 uses a Renesage RA4M1 ARM Cortex-M4F microcontroller, which is a significant upgrade from the previous ATmega328P 8-bit AVR microcontroller. This new microcontroller offers enhanced performance, more memory, and additional features, making it suitable for more complex projects and applications.
</p>
<p>
    My indention was to use the Renesas RA API to control the microcontroller with the Arduino IDE, see the video.
    But I found it poorly documented, here the first simple examples I created.
</p>
<br/>
    <ul>
        <li><b>LED blinking</b>&nbsp;&nbsp;&nbsp;Source at &nbsp;<a href="https://github.com/ora8/Arduino-Uno-R4/tree/main/blink">github</a></li>
       <li><b>LED dimming</b>&nbsp;&nbsp;Source at &nbsp;<a href="https://github.com/ora8/Arduino-Uno-R4/tree/main/dimm">github</a></li>
     </ul>
</div>
<div>
<video width="600" controls>
    <source src={video} type="video/quicktime">
    Your browser does not support the video tag.
</video>
<h3>LED dimming with PWM</h3>
</div>
</div>
</section>

<style>
    .arduino-container {
        display: grid;
        margin-top: 4rem   ;
        margin-bottom: 4rem;
        grid-template-columns: repeat(2, 1fr); /* Creates two equal columns */
        gap: 20px; /* Space between grid items */
    }
    h1 {
        font-weight: bold;
    }
</style>