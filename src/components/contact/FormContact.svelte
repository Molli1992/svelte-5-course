<script lang="ts">
	import DashedSeparator from '../../components/DashedSeparator.svelte';
	import { FontAwesomeIcon } from '@fortawesome/svelte-fontawesome';
	import { faLocationDot, faEnvelope, faPhone } from '@fortawesome/free-solid-svg-icons';
	import BlueButton from '../../components/BlueButton.svelte';
	import { isValidEmail } from '../../utils/regexs';
	import Swal from 'sweetalert2';

	let emailData = $state({ name: '', email: '', message: '' });

	const onSubmit = (e: SubmitEvent) => {
		e.preventDefault();

		if (!emailData.name || !emailData.email || !emailData.message) {
			Swal.fire({
				title: 'Info!',
				text: 'Completar todos los campos!',
				icon: 'info'
			});
		} else if (!isValidEmail(emailData.email)) {
			Swal.fire({
				title: 'Info!',
				text: 'Ingresar un email valido',
				icon: 'info'
			});
		} else {
			Swal.fire({
				title: 'Exito!',
				text: 'Email enviado exitosamente!',
				icon: 'success'
			});

			emailData = { name: '', email: '', message: '' };
		}
	};
</script>

<div class="container">
	<div class="column-container">
		<DashedSeparator />
		<h1 class="black-title">Contactanos</h1>
		<p class="black-text">
			Contenidos es una productora con historia en televisión, teatro y eventos. Fundada por Gerardo
			Sofovich, seguimos creando propuestas que marcan la cultura y el entretenimiento Argentino.
		</p>

		<div class="flex-container">
			<div class="icon">
				<div>
					<FontAwesomeIcon icon={faLocationDot} />
				</div>
			</div>

			<div class="sub-column-container">
				<p class="text">Visit Us:</p>
				<p class="black-text">27 Division St, New York, NY 10002, USA</p>
			</div>
		</div>

		<div class="flex-container">
			<div class="icon">
				<div>
					<FontAwesomeIcon icon={faEnvelope} />
				</div>
			</div>

			<div class="sub-column-container">
				<p class="text">Mail Us:</p>
				<p class="black-text">felipe.blaksley@hotmail.com</p>
			</div>
		</div>

		<div class="flex-container">
			<div class="icon">
				<div>
					<FontAwesomeIcon icon={faPhone} />
				</div>
			</div>

			<div class="sub-column-container">
				<p class="text">Phone Us:</p>
				<p class="black-text">+54 9 112 458 6710</p>
			</div>
		</div>
	</div>

	<div class="column-container">
		<form
			class="form"
			onsubmit={(e) => {
				onSubmit(e);
			}}
		>
			<h1 class="black-subtitle" style="font-weight: bold;">Dejanos tu mensaje</h1>

			<div class="inputs-container">
				<input class="input" placeholder="Nombre *" bind:value={emailData.name} />
				<input class="input" placeholder="Email *" bind:value={emailData.email} />
				<textarea class="text-area input" placeholder="Mensaje..." bind:value={emailData.message}
				></textarea>
				<BlueButton value="Enviar Mensaje" />
			</div>
		</form>
	</div>
</div>

<style>
	.container {
		width: 100%;
		max-width: 1200px;
		padding: 0px 25px;
		display: flex;
		gap: 50px;
	}

	.column-container {
		width: 50%;
		display: flex;
		flex-direction: column;
		gap: 30px;
	}

	.flex-container {
		display: flex;
		align-items: center;
		gap: 25px;
	}

	.icon {
		color: blue;
		background-color: #f2f2f2;
		font-size: 22px;
		border-radius: 5px;
		padding: 15px;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.text {
		font-weight: bold;
		font-size: 18px;
		line-height: 30px;
		color: #000000;
	}

	.sub-column-container {
		display: flex;
		flex-direction: column;
	}

	.form {
		width: 100%;
		background-color: #f2f2f2;
		display: flex;
		flex-direction: column;
		gap: 30px;
		padding: 30px;
		border-radius: 10px;
	}

	.inputs-container {
		width: 100%;
		display: flex;
		flex-direction: column;
		gap: 10px;
	}

	.input {
		background-color: #ffffff;
		color: #6e6e6e;
		outline: none;
		border: none;
		padding: 15px 20px;
		border-radius: 5px;
		font-size: 16px;
	}

	.text-area {
		height: 200px;
	}

	@media (max-width: 1000px) {
		.container {
			flex-direction: column;
			align-items: center;
		}

		.column-container {
			width: 600px;
		}
	}

	@media (max-width: 650px) {
		.column-container {
			width: 100%;
		}
		.text {
			font-size: 16px;
		}
	}

	@media (max-width: 450px) {
		.form {
			padding: 20px;
		}
	}
</style>
