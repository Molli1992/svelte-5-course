<script lang="ts">
	let { imageUrl, title, description }: { imageUrl: string; title: string; description: string } =
		$props();

	const backgroundGradient: string =
		'linear-gradient(to bottom, rgba(25, 25, 70, 0.4), rgba(25, 25, 70, 0.4))';
</script>

<div class="hero-section" style="background-image: {backgroundGradient}, url('{imageUrl}');">
	<div class="hero-content">
		<h1>{title}</h1>
		<p class="white-text">{description}</p>

		<div class="hero-buttons">
			<a href="https://whatsapp.com/" target="_blank" class="whatsapp button"> WhatsApp </a>
			<a href="https://instagram.com" target="_blank" class="instagram button"> Instagram </a>
		</div>
	</div>
</div>

<style>
	.hero-section {
		width: 100%;
		height: 90vh;
		display: flex;
		align-items: center;
		justify-content: center;
		background-size: cover;
		background-repeat: no-repeat;
		background-position: center;
	}

	.hero-content {
		display: flex;
		align-items: center;
		justify-content: center;
		flex-direction: column;
		padding: 10px;
		text-align: center;
		color: #ffffff;
		gap: 20px;
	}

	.hero-content h1 {
		font-size: 48px;
	}

	.hero-content p {
		width: 700px;
	}

	.hero-buttons {
		display: flex;
		gap: 25px;
	}

	.button {
		padding: 15px;
		font-size: 22px;
		border-radius: 10px;
		text-decoration: none;
		display: inline-block;
		border: 1px solid transparent;
		transition:
			background-color 0.8s ease,
			border-color 0.8s ease;
	}

	.whatsapp {
		background-color: #25d366;
	}

	.whatsapp:hover {
		background-color: transparent;
		border-color: #25d366;
	}

	.instagram {
		background-color: #833ab4;
	}

	.instagram:hover {
		background-color: transparent;
		border-color: #833ab4;
	}

	@media (max-width: 735px) {
		.hero-content p {
			width: 100%;
		}
	}

	@media (max-width: 650px) {
		.hero-content h1 {
			font-size: 38px;
		}

		.button {
			font-size: 20px;
		}
	}
</style>
