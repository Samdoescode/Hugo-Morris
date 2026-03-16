<script lang="ts">
	const Stills = import.meta.glob(
		'$lib/images/imagestills/Stills/*.{avif,gif,heif,jpeg,jpg,png,tiff,webp}',
		{
			eager: true,
			query: '?url', import: 'default'
		}
	);

	const imageUrls: string[] = Object.values(Stills) as string[];

	function shuffleArray<T>(array: T[]): T[] {
		const shuffled = [...array];
		for (let i = shuffled.length - 1; i > 0; i--) {
			const j = Math.floor(Math.random() * (i + 1));
			[shuffled[i], shuffled[j]] = [shuffled[j], shuffled[i]];
		}
		return shuffled;
	}

	const shuffledImages = shuffleArray(imageUrls);
</script>

{#each shuffledImages as url}
	<li class="w-1/6 grayscale opacity-35 shadow-lg">
		<img
			class="object-cover w-full rounded-sm"
			src={url}
			alt="Still"
			loading="lazy"
		/>
	</li>
{/each}
