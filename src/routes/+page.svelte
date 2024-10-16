<script>
	import { onMount } from 'svelte';

	let images = [
		{ src: '/portfolio/image1.jpg', alt: 'Lefentswe modeling casual wear' },
		{ src: '/portfolio/image2.jpg', alt: 'Lefentswe in high fashion shoot' },
		{ src: '/portfolio/image3.jpg', alt: 'Lefentswe on the runway' },
	];

	let currentImageIndex = 0;

	onMount(() => {
		const interval = setInterval(() => {
			currentImageIndex = (currentImageIndex + 1) % images.length;
		}, 5000);

		return () => clearInterval(interval);
	});
</script>

<svelte:head>
	<title>Lefentswe - Model Portfolio</title>
	<meta name="description" content="Professional portfolio of Lefentswe, fashion model" />
</svelte:head>

<section class="hero">
	<div class="hero-content">
		<h1>Lefentswe</h1>
		<p>Fashion Model | Influencer | Artist</p>
	</div>
	<div class="hero-image">
		{#each images as image, index}
			<img
				src={image.src}
				alt={image.alt}
				class:active={index === currentImageIndex}
			/>
		{/each}
	</div>
</section>

<section class="about">
	<h2>About Me</h2>
	<p>
		Hello, I'm Lefentswe. With a passion for fashion and a unique sense of style, I've been
		gracing runways and photoshoots for over 5 years. My work spans from high fashion to
		commercial modeling, always bringing authenticity and creativity to every project.
	</p>
</section>

<section class="cta">
	<h2>Let's Work Together</h2>
	<p>
		Looking for a versatile model for your next project? Let's create something amazing together.
	</p>
	<a href="/contact" class="cta-button">Contact Me</a>
</section>

<style>
	.hero {
		display: flex;
		height: 100vh;
		align-items: center;
		background-color: #f0f0f0;
	}

	.hero-content {
		flex: 1;
		padding: 2rem;
	}

	.hero-image {
		flex: 1;
		height: 100%;
		position: relative;
		overflow: hidden;
	}

	.hero-image img {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		object-fit: cover;
		opacity: 0;
		transition: opacity 0.5s ease-in-out;
	}

	.hero-image img.active {
		opacity: 1;
	}

	h1 {
		font-size: 4rem;
		margin-bottom: 0.5rem;
	}

	.hero-content p {
		font-size: 1.5rem;
		color: #666;
	}

	.about, .cta {
		padding: 4rem 2rem;
		max-width: 800px;
		margin: 0 auto;
		text-align: center;
	}

	h2 {
		font-size: 2.5rem;
		margin-bottom: 1rem;
	}

	.cta-button {
		display: inline-block;
		background-color: #333;
		color: white;
		padding: 0.75rem 1.5rem;
		text-decoration: none;
		font-size: 1.1rem;
		border-radius: 5px;
		transition: background-color 0.3s ease;
	}

	.cta-button:hover {
		background-color: #555;
	}

	@media (max-width: 768px) {
		.hero {
			flex-direction: column;
		}

		.hero-image {
			height: 50vh;
		}

		h1 {
			font-size: 3rem;
		}

		.hero-content p {
			font-size: 1.2rem;
		}
	}
</style>