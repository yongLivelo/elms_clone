<script>
	import { fade, blur, fly, scale } from 'svelte/transition';

	
	let visible = true;



	import image1 from './images/image-1.jpg';
	import image2 from './images/image-2.jpg';
	import image3 from './images/image-3.jpg';

	import left from './images/nav/left.png';
	import pause from './images/nav/pause.png';
	import resume from './images/nav/play.png';
	import right from './images/nav/right.png';

	let mControl = resume;
	const images = [image1, image2, image3];
	let imageDisplay = image1;
	let i = 0;
	const changeImage = () => {
		i++;
		i = i >= images.length ? 0 : i;
		imageDisplay = images[i];
	};

	const changeImageLeft = () => {
		i--;
		i = i < 0 ? images.length - 1 : i;

		imageDisplay = images[i];
	};
	let timer = setInterval(changeImage, 5000);

	const goDirection = (d) => {
		if (d === 'right') {
			changeImage();
			clearInterval(timer);
			timer = setInterval(changeImage, 5000);
		} else {
			changeImageLeft();
			clearInterval(timer);
			timer = setInterval(changeImage, 5000);
		}
	};
	let state = true;
	const pauseFn = () => {
		if (state) {
			mControl = pause;
			clearInterval(timer);
			state = false;
			console.log("stop");
		} else {
			mControl = resume;
			timer = setInterval(changeImage, 5000);
			state = true;
			console.log("resume");
		}
	};

	let hover = false;
</script>
<!-- fix -->
<div
	on:mouseenter={() => {
		hover = true;
	}}
	on:mouseleave={() => {
		hover = false;
	}}
	class="slider"
>
	{#key imageDisplay}

		<div transition:fade={{ duration: 600 }}>
			<img src={imageDisplay} alt="" />
		</div>
	{/key}
	{#if i == 1}
	<div transition:fly={{ x: '-100'}} class="text">
		<h1>Online Registration</h1>
		<p>
			We warmly welcome high school graduates, college transferees, second coursers, foreign
			applicants, and graduate program applicants to our campuses.
		</p>
		<a class="button" href="https://www.sti.edu/admissions_registration.asp">Register now</a>
	</div>
{/if}
	{#if hover}
		<div class="controls">
			<div on:click={() => goDirection('left')}><img src={left} alt="ASD" /></div>
			<div on:click={() => pauseFn()}><img src={mControl} alt="ASD" /></div>
			<div on:click={() => goDirection('right')}><img src={right} alt="ASD" /></div>
		</div>
	{/if}
</div>

<style lang="scss">
	
$primary-color: #0C3057;
$secondary-color: #3983d2;
$text-color-1: black;
$text-color-2: white;


a{
    text-decoration: none;
    color: inherit;

}

	.slider:hover ~ .controls {
		display: block;
	}
	.slider {
		position: relative;
		margin-top: 70px;
		width: 100%;
		height: 1000px;

		img {
			position: absolute;
			width: 100%;
			transition: 0.4s;
			height: 100%;
			object-fit: cover;
			z-index: -10;
		}

		.text {
			* {
				margin-bottom: 50px;
			}
			position: absolute;
			margin-left: 15%;
			top: 30%;
			width: 500px;
			font-size: x-large;
			h1,
			p {
				text-shadow: 1px 1px 1px rgba(0, 0, 0, 0.7);
				color: white;
			}

			.button {
				padding: 10px 15px;
				background-color: rgba(255, 255, 255, 0.63);
				border-radius: 5px;
				width: fit-content;
				transition: 0.4s all;
			}

			.button:hover {
				background-color: white;
			}
		}

		.controls {
			margin-bottom: 30px;
			border-radius: 10px;
			display: flex;
			position: absolute;
			left: 50%;
			transform: translateX(-50%);
			bottom: 0;
			width: fit-content;
			gap: 40px;
			width: 200px;
			padding: 0px 20px;
			height: 80px;
			background-color: rgba(0, 0, 0, 0.36);
			div {
				cursor: pointer;
				img {
					width: 100%;
					position: relative;
					object-fit: contain;
					z-index: 10;
				}
			}
		}
	}
</style>
