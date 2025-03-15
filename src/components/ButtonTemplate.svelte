<script lang="ts">
	let isFlipped = $state(false);
	const onclick = () => {
		isFlipped = !isFlipped;
	};
</script>

<div class="buttons-wrapper">
	<article class="button-frame" style={`${isFlipped ? '--current-rotation: y 180deg;' : ''}`}>
		<div class="button-frame-inner">
			<div class="button-frame-front">
				<span class="button-frame-number">500</span>
				<div class="button-frame-button"></div>
				<div class="button-frame-text">
					<p>A blurb about the button :)</p>
				</div>
				<button {onclick} class="button-frame-flip hover:cursor-cell">Flippa the table</button>
			</div>
			<div class="button-frame-back">
				<div class="button-backside">bloop</div>
				<button {onclick} class="button-frame-flip hover:cursor-cell">Flippa the table</button>
			</div>
		</div>
	</article>
</div>

<style scoped>
	.button-frame {
		--current-rotation: y 0deg;
		display: grid;
		min-height: 500px;
		width: 400px;
		grid-template-rows: [frame-area-start button-area-start number-area-start back-area-start] 60px [number-area-end] 340px [button-area-end text-area-start] auto [text-area-end back-area-end flip-area-start] 60px [flip-area-end frame-area-end];
		grid-template-columns: [frame-area-start button-area-start text-area-start back-area-start flip-area-start] 1fr [number-area-start] auto [frame-area-end button-area-end number-area-end text-area-end back-area-end flip-area-end];
	}
	.button-frame-inner,
	.button-frame-front,
	.button-frame-back {
		display: grid;
		grid-area: frame-area;
		grid-template-columns: subgrid;
		grid-template-rows: subgrid;
	}
	.button-frame-inner {
		position: relative;
		transition: rotate 0.8s;
		transform-style: preserve-3d;
		rotate: var(--current-rotation);
	}
	.button-frame-front,
	.button-frame-back {
		border: 2px solid black;
		width: 100%;
		height: 100%;
		backface-visibility: hidden;
	}
	.button-frame-front {
		background-color: white;
	}
	.button-frame-back {
		rotate: y 180deg;
	}
	.button-frame-button {
		display: flex;
		align-items: center;
		justify-content: center;
		grid-area: button-area;
	}
	.button-frame-number {
		display: flex;
		align-items: center;
		justify-content: center;
		padding-inline: 3rem;
		border-left: 2px solid black;
		border-bottom: 2px solid black;
		grid-area: number-area;
	}
	.button-frame-text {
		border-top: 2px solid black;
		grid-area: text-area;
	}
	.button-frame-flip {
		border-top: 2px solid black;
		grid-area: flip-area;
	}
	.button-backside {
		grid-area: back-area;
		background-color: #bc6161aa;
		transform: rotateY(180deg);
	}
</style>
