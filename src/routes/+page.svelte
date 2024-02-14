<script lang="ts">
	import './style.css';

	let isMaybeYes: boolean | null = $state(null);
	let confirmed: boolean | null = $state(null);
	let hasClickedNo: boolean | null = $state(false);
</script>

<main class="main">
	<section class="section__header">
		<h1 class="header__title">
			Will you be my valentine {isMaybeYes ? '💖' : isMaybeYes === null ? '🥹' : '🫣'}?
		</h1>
		<article class="header__controls" onmouseleave={() => (isMaybeYes = null)}>
			{#if hasClickedNo}
				<button
					class="control__button control__accept"
					onmouseenter={() => (isMaybeYes = true)}
					onclick={() => (confirmed = true)}>{confirmed ? "It's a date!" : 'Yes'}</button
				>
			{/if}
			{#if !confirmed}
				<button
					class="control__button control__reject"
					onmouseenter={() => (isMaybeYes = false)}
					onclick={() => {
						confirmed = false;
						hasClickedNo = true;
					}}>{hasClickedNo ? 'Wow 😭' : 'No'}</button
				>
			{/if}
		</article>
	</section>
	{#if confirmed}
		<section class="section__content">
			<h2>Great!</h2>
			<p class="header">
				I'll see you Friday, Feb 16th @6pm at <a
					class="link__text"
					href="https://www.auliban.online/"
					target="_blank">Au Liban</a
				>
				🥰
			</p>
			<iframe
				id="iframe"
				title="song"
				style="border-radius:12px"
				src="https://open.spotify.com/embed/track/1dGr1c8CrMLDpV6mPbImSI?utm_source=generator"
				width="90%"
				height="300"
				frameBorder="0"
				allowfullscreen={false}
				allow="autoplay; clipboard-write; encrypted-media; fullscreen; picture-in-picture"
				loading="lazy"
			/>
		</section>
	{/if}
	{#if confirmed === false}
		<section class="section__content">
			<h2>Oops! Looks like an error on our part. Please Try Again.</h2>
			<p>Please contact your system administration 👨🏾‍💻.</p>
			<p class="text--tiny">Someone forgot to make this button work 🙄...</p>
		</section>
	{/if}
</main>

<style lang="postcss">
	.main {
		height: 100vh;
		width: 100vw;

		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.section__header {
		min-height: 40%;
		width: 100%;
		text-align: center;

		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		gap: 40px;
	}

	.header__title {
		font-size: 40px;
		color: #de6294;
	}

	.header__controls {
		padding-block: 16px;
		width: 100%;
		cursor:
			url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg'  width='40' height='48' viewport='0 0 100 100' style='fill:black;font-size:24px;'><text y='50%'>🤔</text></svg>")
				16 0,
			auto;

		display: flex;
		justify-content: center;
		align-items: center;
		gap: 24px;
	}

	.section__content {
		height: 60%;
		width: 100%;
		color: #de6294;

		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		gap: 24px;
	}

	.control__button {
		padding: 12px 32px;
		border: none;
		border-radius: 6px;
		cursor: pointer;
	}

	.control__accept {
		background-color: #e6a9d3;
		cursor:
			url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg'  width='40' height='48' viewport='0 0 100 100' style='fill:black;font-size:24px;'><text y='50%'>❤️</text></svg>")
				16 0,
			auto;
	}

	.control__reject {
		background-color: #887175;
		color: white;
		cursor:
			url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg'  width='40' height='48' viewport='0 0 100 100' style='fill:black;font-size:24px;'><text y='50%'>😱</text></svg>")
				16 0,
			auto;
	}

	.link__text {
		text-decoration: none;
		color: #3b8ac1;
	}

	.text--tiny {
		font-size: 12px;
	}
</style>
