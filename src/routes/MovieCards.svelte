<script lang="ts">
	const Stills = import.meta.glob(
		'$lib/images/imagestills/Stills/*.{avif,gif,heif,jpeg,jpg,png,tiff,webp}',
		{
			as: "url",
			eager: true,
		}
	);

	const imageUrls: string[] = Object.values(Stills);

	function shuffleArray<T>(array: T[]): T[] {
		const shuffled = [...array];
		for (let i = shuffled.length - 1; i > 0; i--) {
			const j = Math.floor(Math.random() * (i + 1));
			[shuffled[i], shuffled[j]] = [shuffled[j], shuffled[i]];
		}
		return shuffled;
	}

	const shuffledImages = shuffleArray(imageUrls).map((url) => ({
		url,
		height: 224 * (Math.random() + 0.5)
	}));
</script>

{#each shuffledImages as image}
	<li  class="w-1/6 transition-transform grayscale opacity-35 duration-300 hover:scale-110 hover:grayscale-0 hover:opacity-100 shadow-lg">
		<img
			class="object-cover w-full rounded-sm "
			src={image.url}
			alt="Still"
			loading="lazy"
		/>
	</li>
{/each}
