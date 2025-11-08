<script lang="ts">
	import { page } from '$app/stores';
	import Card from '$lib/components/ui/card/card.svelte';
	import CardContent from '$lib/components/ui/card/card-content.svelte';
	import Button from '$lib/components/ui/button/button.svelte';
	import Badge from '$lib/components/ui/badge/badge.svelte';
	import {
		Calendar,
		User,
		Clock,
		ArrowLeft,
		Share2,
		Facebook,
		Twitter,
		Mail,
		Sparkles
	} from '@lucide/svelte';
	import { onMount } from 'svelte';

	// This would normally come from a data loader or API
	const post = {
		id: 1,
		title: "The Ultimate Guide to Sorrento's Lemon Groves",
		excerpt:
			"Discover the history, culture, and best places to experience Sorrento's famous lemons and limoncello production.",
		image: 'https://images.unsplash.com/photo-1590502593747-42a996133562?w=1200&q=80',
		category: 'Local Culture',
		author: 'Maria Romano',
		date: '2024-10-15',
		readTime: '8 min read',
		content: `
			<p>When you think of Sorrento, one image inevitably comes to mind: the vibrant yellow lemons that hang heavy on trees throughout the peninsula. These aren't just any lemons – they're the famous Limone di Sorrento IGP (Protected Geographical Indication), a variety unique to this sun-drenched corner of Italy.</p>

			<h2>The History of Sorrento Lemons</h2>
			<p>Lemon cultivation in Sorrento dates back to the 11th century, when monks first planted the citrus groves that would become the region's trademark. The volcanic soil, Mediterranean climate, and traditional cultivation methods create lemons unlike any other in the world – larger, more fragrant, and with a thicker, more aromatic peel perfect for limoncello production.</p>

			<h2>Visiting the Lemon Groves</h2>
			<p>Several historic lemon groves around Sorrento welcome visitors for tours and tastings. Walking through these terraced gardens, shaded by traditional wooden pergolas called "pagliarelle," is like stepping into a living postcard. The air is perfumed with the scent of lemon blossoms, especially in spring.</p>

			<h3>Recommended Lemon Grove Tours:</h3>
			<ul>
				<li><strong>Giardini di Cataldo:</strong> Family-run for five generations, offering guided tours and limoncello tastings</li>
				<li><strong>Limoneto Massa Lubrense:</strong> Stunning views over the Bay of Naples with organic cultivation</li>
				<li><strong>Agrumeto Gargiulo:</strong> Traditional methods and delicious lemon products</li>
			</ul>

			<h2>Making Limoncello</h2>
			<p>No visit to a Sorrento lemon grove is complete without learning about limoncello, the sweet lemon liqueur that's become synonymous with the Amalfi Coast. The traditional recipe is surprisingly simple: lemon peels, alcohol, sugar, and water. But the secret lies in using the right lemons – those thick, fragrant peels of Limone di Sorrento make all the difference.</p>

			<h2>Best Time to Visit</h2>
			<p>Lemon groves can be visited year-round, but each season offers something special:</p>
			<ul>
				<li><strong>Spring (March-May):</strong> Lemon blossoms fill the air with intoxicating fragrance</li>
				<li><strong>Summer (June-August):</strong> Trees heavy with ripe lemons, peak growing season</li>
				<li><strong>Fall (September-October):</strong> Harvest time, cooler weather, fewer crowds</li>
				<li><strong>Winter (November-February):</strong> Still productive, and the yellow fruit provides cheerful color</li>
			</ul>

			<h2>What to Buy</h2>
			<p>Beyond limoncello, lemon groves sell a variety of delicious products:</p>
			<ul>
				<li>Lemon marmalade and preserves</li>
				<li>Lemon-scented soaps and cosmetics</li>
				<li>Candied lemon peels</li>
				<li>Lemon honey</li>
				<li>Lemon olive oil</li>
			</ul>

			<h2>Planning Your Visit</h2>
			<p>Most lemon grove tours last 45 minutes to 1 hour and include a tasting of various lemon products. Many require advance booking, especially in high season. Tours typically cost €10-25 per person and often include transport from Sorrento center.</p>

			<p>Whether you're a foodie, a photography enthusiast, or simply someone who appreciates authentic cultural experiences, a visit to Sorrento's lemon groves offers a refreshing glimpse into the traditions that make this region special. Plus, you'll never look at lemons the same way again!</p>
		`
	};

	const relatedPosts = [
		{
			id: 5,
			title: 'Authentic Sorrentine Recipes to Try at Home',
			image: 'https://images.unsplash.com/photo-1556911220-bff31c812dba?w=400&q=80',
			category: 'Food & Drink'
		},
		{
			id: 2,
			title: 'Best Beach Clubs in Sorrento: A Complete Guide',
			image: 'https://images.unsplash.com/photo-1519046904884-53103b34b206?w=400&q=80',
			category: 'Beaches'
		}
	];

	onMount(() => {
		const handleScroll = () => {
			const reveals = document.querySelectorAll('.scroll-reveal');
			reveals.forEach((element) => {
				const elementTop = element.getBoundingClientRect().top;
				const elementVisible = 150;
				if (elementTop < window.innerHeight - elementVisible) {
					element.classList.add('revealed');
				}
			});
		};
		window.addEventListener('scroll', handleScroll);
		handleScroll();
		return () => window.removeEventListener('scroll', handleScroll);
	});
</script>

<svelte:head>
	<title>{post.title} | Welcome2Sorrento Blog</title>
	<meta name="description" content={post.excerpt} />
</svelte:head>

<div class="-mt-24">
	<!-- Hero Image -->
	<section class="relative flex min-h-[70vh] items-end overflow-hidden pt-24">
		<div class="absolute inset-0 z-0">
			<img src={post.image} alt={post.title} class="h-full w-full object-cover" />
			<div
				class="absolute inset-0 bg-gradient-to-t from-[color:var(--dark)]/90 via-[color:var(--dark)]/60 to-transparent"
			></div>
		</div>

		<div class="relative z-10 container mx-auto px-4 pb-16 sm:px-6 lg:px-8">
			<div class="animate-fade-in-up max-w-4xl">
				<Badge
					class="mb-4 border-0 bg-gradient-to-r from-[color:var(--purple-lavender)] to-[color:var(--turquoise)] px-4 py-1.5 text-white"
				>
					{post.category}
				</Badge>
				<h1 class="mb-6 text-3xl font-bold text-white sm:text-4xl lg:text-6xl">
					{post.title}
				</h1>
				<div class="flex flex-wrap items-center gap-4 text-white/90">
					<div class="flex items-center space-x-2">
						<User class="h-5 w-5" />
						<span>{post.author}</span>
					</div>
					<div class="flex items-center space-x-2">
						<Calendar class="h-5 w-5" />
						<span
							>{new Date(post.date).toLocaleDateString('en-US', {
								month: 'long',
								day: 'numeric',
								year: 'numeric'
							})}</span
						>
					</div>
					<div class="flex items-center space-x-2">
						<Clock class="h-5 w-5" />
						<span>{post.readTime}</span>
					</div>
				</div>
			</div>
		</div>
	</section>

	<!-- Article Content -->
	<article class="relative bg-white py-20">
		<div class="container mx-auto px-4 sm:px-6 lg:px-8">
			<div class="mx-auto max-w-4xl">
				<!-- Back Button -->
				<div class="scroll-reveal mb-10">
					<Button variant="ghost" class="group hover:bg-muted">
						<a href="/blog" class="flex items-center space-x-2">
							<ArrowLeft class="h-4 w-4 transition-transform group-hover:-translate-x-1" />
							<span>Back to Blog</span>
						</a>
					</Button>
				</div>

				<!-- Share Buttons -->
				<div class="scroll-reveal mb-12">
					<Card
						class="overflow-hidden border-2 border-[color:var(--purple-lavender)]/20 transition-colors hover:border-[color:var(--purple-lavender)]"
					>
						<div class="relative">
							<div
								class="absolute inset-0 bg-gradient-to-r from-[color:var(--purple-lavender)]/5 to-[color:var(--turquoise)]/5"
							></div>
							<CardContent class="relative p-6">
								<div
									class="flex flex-col items-start justify-between gap-4 sm:flex-row sm:items-center"
								>
									<span class="flex items-center space-x-2 font-semibold text-[color:var(--dark)]">
										<Share2 class="h-5 w-5" />
										<span>Share this article</span>
									</span>
									<div class="flex items-center space-x-3">
										<button
											class="flex h-10 w-10 items-center justify-center rounded-xl bg-gradient-to-r from-blue-500 to-blue-600 text-white transition-all duration-300 hover:scale-110 hover:shadow-lg"
										>
											<Facebook class="h-5 w-5" />
										</button>
										<button
											class="flex h-10 w-10 items-center justify-center rounded-xl bg-gradient-to-r from-cyan-500 to-blue-500 text-white transition-all duration-300 hover:scale-110 hover:shadow-lg"
										>
											<Twitter class="h-5 w-5" />
										</button>
										<button
											class="flex h-10 w-10 items-center justify-center rounded-xl bg-gradient-to-r from-purple-500 to-pink-500 text-white transition-all duration-300 hover:scale-110 hover:shadow-lg"
										>
											<Mail class="h-5 w-5" />
										</button>
									</div>
								</div>
							</CardContent>
						</div>
					</Card>
				</div>

				<!-- Article Body -->
				<div class="prose prose-lg scroll-reveal max-w-none">
					{@html post.content}
				</div>
			</div>
		</div>
	</article>

	<!-- Related Posts -->
	<section class="relative bg-gradient-to-b from-[color:var(--off-white)] to-white py-20">
		<div class="container mx-auto px-4 sm:px-6 lg:px-8">
			<div class="mx-auto max-w-4xl">
				<div class="scroll-reveal mb-12">
					<div
						class="mb-6 inline-flex items-center space-x-2 rounded-full border border-[color:var(--purple-lavender)]/20 bg-[color:var(--purple-lavender)]/10 px-4 py-2"
					>
						<Sparkles class="h-4 w-4 text-[color:var(--purple-lavender)]" />
						<span class="text-sm font-medium text-[color:var(--dark)]">More to Explore</span>
					</div>
					<h2 class="text-3xl font-bold text-[color:var(--dark)] sm:text-4xl">Related Articles</h2>
				</div>
				<div class="grid grid-cols-1 gap-6 md:grid-cols-2">
					{#each relatedPosts as relatedPost, index}
						<div class="scroll-reveal" style="transition-delay: {index * 0.1}s">
							<a href="/blog/{relatedPost.id}" class="group block">
								<Card
									class="h-full overflow-hidden border-2 border-transparent transition-all duration-500 hover:border-[color:var(--purple-lavender)] hover:shadow-2xl"
								>
									<div class="relative h-56 overflow-hidden">
										<img
											src={relatedPost.image}
											alt={relatedPost.title}
											class="h-full w-full object-cover transition-transform duration-700 group-hover:scale-110"
										/>
										<div
											class="absolute inset-0 bg-gradient-to-t from-[color:var(--dark)]/60 to-transparent"
										></div>
										<div class="absolute top-4 left-4">
											<Badge
												class="border-0 bg-gradient-to-r from-[color:var(--purple-lavender)] to-[color:var(--turquoise)] text-white"
											>
												{relatedPost.category}
											</Badge>
										</div>
									</div>
									<CardContent class="p-6">
										<h3
											class="text-xl font-bold text-[color:var(--dark)] transition-colors duration-300 group-hover:text-[color:var(--purple-lavender)]"
										>
											{relatedPost.title}
										</h3>
									</CardContent>
								</Card>
							</a>
						</div>
					{/each}
				</div>
			</div>
		</div>
	</section>

	<!-- CTA -->
	<section class="relative overflow-hidden py-20">
		<div
			class="animate-gradient absolute inset-0 bg-gradient-to-br from-[color:var(--purple-lavender)] via-[color:var(--deep-purple)] to-[color:var(--dark)]"
		></div>

		<div class="scroll-reveal relative z-10 container mx-auto px-4 text-center sm:px-6 lg:px-8">
			<div class="mx-auto max-w-3xl text-white">
				<h2 class="mb-4 text-3xl font-bold sm:text-4xl">Ready to Experience Sorrento?</h2>
				<p class="mb-8 text-xl text-white/90">
					Let us help you plan your perfect Sorrento adventure with our personalized booking service
				</p>
				<Button
					size="lg"
					class="bg-white px-10 py-7 text-lg text-[color:var(--dark)] shadow-2xl transition-all duration-500 hover:scale-105 hover:bg-[color:var(--off-white)]"
				>
					<a href="/contact">Get in Touch</a>
				</Button>
			</div>
		</div>
	</section>
</div>

<style>
	:global(.prose h2) {
		margin-top: 3rem;
		margin-bottom: 1.5rem;
		font-size: 1.875rem;
		font-weight: 700;
		color: var(--dark);
	}

	:global(.prose h3) {
		margin-top: 2rem;
		margin-bottom: 1rem;
		font-size: 1.5rem;
		font-weight: 700;
		color: var(--dark);
	}

	:global(.prose p) {
		margin-bottom: 1.5rem;
		font-size: 1.125rem;
		line-height: 1.75rem;
		color: hsl(var(--muted-foreground));
	}

	:global(.prose ul) {
		margin-top: 1.5rem;
		margin-bottom: 1.5rem;
		margin-left: 1.5rem;
	}

	:global(.prose ul > * + *) {
		margin-top: 0.75rem;
	}

	:global(.prose li) {
		font-size: 1.125rem;
		line-height: 1.75rem;
		color: hsl(var(--muted-foreground));
	}

	:global(.prose strong) {
		font-weight: 600;
		color: hsl(var(--foreground));
	}
</style>
