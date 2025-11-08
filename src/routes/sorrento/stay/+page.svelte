<script lang="ts">
	import Card from '$lib/components/ui/card/card.svelte';
	import CardContent from '$lib/components/ui/card/card-content.svelte';
	import CardTitle from '$lib/components/ui/card/card-title.svelte';
	import Button from '$lib/components/ui/button/button.svelte';
	import Badge from '$lib/components/ui/badge/badge.svelte';
	import { Star, MapPin, Wifi, Coffee, Waves, Heart, Home, Sparkles, Award } from '@lucide/svelte';
	import { onMount } from 'svelte';

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

	const accommodations = [
		{
			name: 'Grand Hotel Excelsior Vittoria',
			category: 'Luxury Hotel',
			priceRange: '€€€€',
			rating: 4.9,
			image: 'https://images.unsplash.com/photo-1582719478250-c89cae4dc85b?w=800&q=80',
			description:
				'Iconic 5-star hotel with panoramic views, lush gardens, and Michelin-starred dining.',
			amenities: ['Pool', 'Spa', 'Restaurant', 'Sea View'],
			location: 'Piazza Tasso',
			gradient: 'from-purple-500 to-indigo-600'
		},
		{
			name: 'Bellevue Syrene',
			category: 'Luxury Hotel',
			priceRange: '€€€€',
			rating: 4.8,
			image: 'https://images.unsplash.com/photo-1566073771259-6a8506099945?w=800&q=80',
			description: 'Elegant clifftop hotel with private beach access and breathtaking bay views.',
			amenities: ['Private Beach', 'Spa', 'Pool', 'Fine Dining'],
			location: 'Piazza della Vittoria',
			gradient: 'from-blue-500 to-cyan-500'
		},
		{
			name: 'Hotel Maison La Minervetta',
			category: 'Boutique Hotel',
			priceRange: '€€€',
			rating: 4.8,
			image: 'https://images.unsplash.com/photo-1571896349842-33c89424de2d?w=800&q=80',
			description:
				'Intimate boutique hotel carved into the cliffside with stunning contemporary design.',
			amenities: ['Sea View', 'Breakfast Included', 'Rooftop Terrace', 'WiFi'],
			location: 'Via Capo',
			gradient: 'from-teal-500 to-emerald-500'
		},
		{
			name: 'Casa Astarita B&B',
			category: 'Bed & Breakfast',
			priceRange: '€€',
			rating: 4.7,
			image: 'https://images.unsplash.com/photo-1590490277693-c3b266b5d916?w=800&q=80',
			description:
				'Charming B&B in historic palazzo with personalized service and homemade breakfast.',
			amenities: ['Free Breakfast', 'Central Location', 'Family-Run', 'Garden'],
			location: 'Corso Italia',
			gradient: 'from-pink-500 to-rose-500'
		},
		{
			name: 'Villa Bohème Luxury Apartments',
			category: 'Apartment',
			priceRange: '€€€',
			rating: 4.9,
			image: 'https://images.unsplash.com/photo-1502672260266-1c1ef2d93688?w=800&q=80',
			description: 'Stylish apartments with fully equipped kitchens, perfect for longer stays.',
			amenities: ['Kitchen', 'Terrace', 'WiFi', 'Central Location'],
			location: 'Via Fuorimura',
			gradient: 'from-amber-500 to-orange-500'
		},
		{
			name: 'Il Nido Hotel Sorrento',
			category: 'Mid-Range Hotel',
			priceRange: '€€',
			rating: 4.6,
			image: 'https://images.unsplash.com/photo-1455587734955-081b22074882?w=800&q=80',
			description: 'Comfortable hotel with rooftop pool and easy access to town center.',
			amenities: ['Rooftop Pool', 'Restaurant', 'Bar', 'WiFi'],
			location: 'Via Degli Aranci',
			gradient: 'from-green-500 to-teal-500'
		}
	];

	const categories = [
		'All',
		'Luxury Hotel',
		'Boutique Hotel',
		'Mid-Range Hotel',
		'Bed & Breakfast',
		'Apartment'
	];
	let selectedCategory = $state('All');

	const filteredAccommodations = $derived(
		selectedCategory === 'All'
			? accommodations
			: accommodations.filter((a) => a.category === selectedCategory)
	);
</script>

<svelte:head>
	<title>Where to Stay in Sorrento - Hotels, B&Bs & Apartments | Welcome2Sorrento</title>
	<meta
		name="description"
		content="Find your perfect accommodation in Sorrento - luxury hotels, boutique B&Bs, and charming apartments with stunning views."
	/>
</svelte:head>

<div class="-mt-24">
	<!-- Hero Section -->
	<section class="relative flex min-h-[70vh] items-center justify-center overflow-hidden pt-24">
		<div class="absolute inset-0 z-0">
			<img
				src="https://images.unsplash.com/photo-1520250497591-112f2f40a3f4?w=1920&q=80"
				alt="Luxury hotel in Sorrento"
				class="h-full w-full object-cover"
			/>
			<div
				class="absolute inset-0 bg-gradient-to-br from-[color:var(--dark)]/80 via-[color:var(--deep-purple)]/60 to-[color:var(--dark)]/80"
			></div>
		</div>

		<div class="relative z-10 container mx-auto px-4 py-32 text-center text-white sm:px-6 lg:px-8">
			<div class="animate-fade-in-up">
				<div
					class="mx-auto mb-6 flex h-20 w-20 items-center justify-center rounded-3xl bg-gradient-to-br from-blue-500 to-cyan-500 shadow-2xl"
				>
					<Home class="h-10 w-10 text-white" />
				</div>
				<h1 class="mb-6 text-5xl font-bold sm:text-6xl lg:text-7xl">
					Where to <span class="text-gradient">Stay</span> in Sorrento
				</h1>
				<p class="heading-serif mx-auto max-w-3xl text-xl font-light text-white/90 sm:text-2xl">
					From luxury clifftop hotels to charming family-run B&Bs
				</p>
			</div>
		</div>
	</section>

	<!-- Introduction -->
	<section class="mesh-gradient relative py-20">
		<div class="container mx-auto px-4 sm:px-6 lg:px-8">
			<div class="scroll-reveal mx-auto max-w-4xl text-center">
				<p class="text-xl leading-relaxed text-muted-foreground">
					Sorrento offers accommodations to suit every style and budget. Whether you seek five-star
					luxury with infinity pools and Michelin-starred restaurants, intimate boutique hotels with
					personalized service, or charming B&Bs where you'll feel like part of the family, you'll
					find your perfect home away from home.
				</p>
			</div>
		</div>
	</section>

	<!-- Category Filter -->
	<section
		class="sticky top-0 z-40 border-b border-gray-200 bg-white/95 py-8 shadow-md backdrop-blur-md"
	>
		<div class="container mx-auto px-4 sm:px-6 lg:px-8">
			<div class="flex flex-wrap justify-center gap-3">
				{#each categories as category}
					<Button
						variant={selectedCategory === category ? 'default' : 'outline'}
						onclick={() => (selectedCategory = category)}
						class={selectedCategory === category
							? 'bg-gradient-to-r from-blue-500 to-cyan-500 text-white transition-all duration-300 hover:shadow-lg'
							: 'border-2 transition-all duration-300 hover:border-blue-500 hover:text-blue-500'}
					>
						{category}
					</Button>
				{/each}
			</div>
		</div>
	</section>

	<!-- Accommodations Grid -->
	<section class="relative bg-white py-32">
		<div class="container mx-auto px-4 sm:px-6 lg:px-8">
			<div class="grid grid-cols-1 gap-8 md:grid-cols-2 lg:grid-cols-3">
				{#each filteredAccommodations as accommodation, index}
					<div class="scroll-reveal h-full" style="transition-delay: {index * 0.1}s">
						<Card
							class="group flex h-full flex-col overflow-hidden border-2 border-transparent transition-all duration-500 hover:border-blue-500 hover:shadow-2xl"
						>
							<div class="relative h-72 overflow-hidden">
								<img
									src={accommodation.image}
									alt={accommodation.name}
									class="h-full w-full object-cover transition-transform duration-700 group-hover:scale-110"
								/>
								<div
									class="absolute inset-0 bg-gradient-to-t from-[color:var(--dark)]/80 via-[color:var(--dark)]/20 to-transparent"
								></div>

								<!-- Category Badge -->
								<div class="absolute top-4 right-4">
									<Badge
										class="border-0 bg-white/90 font-semibold text-[color:var(--dark)] shadow-lg backdrop-blur-sm"
									>
										{accommodation.category}
									</Badge>
								</div>

								<!-- Price Badge -->
								<div class="absolute top-4 left-4">
									<Badge
										class="bg-gradient-to-r {accommodation.gradient} border-0 font-semibold text-white shadow-lg"
									>
										{accommodation.priceRange}
									</Badge>
								</div>

								<!-- Rating -->
								<div
									class="glass absolute bottom-4 left-4 flex items-center space-x-1 rounded-xl border border-white/20 px-3 py-2"
								>
									<Star class="h-5 w-5 fill-yellow-400 text-yellow-400" />
									<span class="text-lg font-bold text-white">{accommodation.rating}</span>
								</div>
							</div>

							<CardContent class="flex flex-grow flex-col p-6">
								<div class="flex-grow">
									<CardTitle
										class="mb-3 text-2xl group-hover:bg-gradient-to-r group-hover:text-transparent group-hover:{accommodation.gradient} transition-all duration-500 group-hover:bg-clip-text"
									>
										{accommodation.name}
									</CardTitle>
									<p class="mb-6 text-sm leading-relaxed text-muted-foreground">
										{accommodation.description}
									</p>

									<div class="mb-6 flex flex-wrap gap-2">
										{#each accommodation.amenities as amenity}
											<Badge
												variant="outline"
												class="border-blue-500 text-xs text-blue-500 transition-colors hover:bg-blue-50"
											>
												{amenity}
											</Badge>
										{/each}
									</div>
								</div>

								<div
									class="flex items-start space-x-2 border-t-2 border-[color:var(--off-white)] pt-4 text-sm text-muted-foreground"
								>
									<MapPin class="mt-0.5 h-4 w-4 flex-shrink-0 text-blue-500" />
									<span class="font-medium">{accommodation.location}</span>
								</div>
							</CardContent>
						</Card>
					</div>
				{/each}
			</div>
		</div>
	</section>

	<!-- Neighborhood Guide -->
	<section class="relative bg-gradient-to-b from-white via-[color:var(--off-white)] to-white py-32">
		<div class="container mx-auto px-4 sm:px-6 lg:px-8">
			<div class="scroll-reveal mb-20 text-center">
				<div
					class="mb-6 inline-flex items-center space-x-2 rounded-full border border-blue-500/20 bg-blue-500/10 px-4 py-2"
				>
					<MapPin class="h-4 w-4 text-blue-500" />
					<span class="text-sm font-medium text-[color:var(--dark)]">Neighborhoods</span>
				</div>
				<h2 class="mb-6 text-4xl font-bold text-[color:var(--dark)] sm:text-5xl">
					Where to <span class="text-gradient">Stay</span>
				</h2>
			</div>

			<div class="mx-auto grid max-w-6xl grid-cols-1 gap-8 md:grid-cols-3">
				{#each [{ title: 'City Center', description: 'Heart of Sorrento with easy access to Piazza Tasso, shops, and restaurants. Perfect for first-time visitors.', icon: MapPin, badge: 'Most Popular', gradient: 'from-blue-500 to-cyan-500' }, { title: 'Marina Grande', description: 'Charming fishing village atmosphere with beachfront restaurants and authentic local character.', icon: Waves, badge: 'Authentic', gradient: 'from-teal-500 to-green-500' }, { title: 'Via Capo', description: 'Clifftop location with spectacular views and quieter atmosphere. Ideal for romantic getaways.', icon: Heart, badge: 'Scenic', gradient: 'from-pink-500 to-rose-500' }] as area, index}
					<div class="scroll-reveal" style="transition-delay: {index * 0.1}s">
						<div class="relative h-full overflow-hidden rounded-3xl">
							<div class="absolute inset-0 bg-gradient-to-r {area.gradient} opacity-5"></div>
							<div
								class="relative h-full rounded-3xl border-2 border-transparent bg-white p-8 transition-all duration-300 hover:border-blue-500"
							>
								<div class="mb-4 flex items-center space-x-3">
									<div
										class="h-12 w-12 rounded-xl bg-gradient-to-br {area.gradient} flex items-center justify-center shadow-lg"
									>
										{#if area.icon === MapPin}
											<MapPin class="h-6 w-6 text-white" />
										{:else if area.icon === Waves}
											<Waves class="h-6 w-6 text-white" />
										{:else if area.icon === Heart}
											<Heart class="h-6 w-6 text-white" />
										{/if}
									</div>
									<h3 class="text-xl font-bold text-[color:var(--dark)]">{area.title}</h3>
								</div>
								<p class="mb-4 text-sm leading-relaxed text-muted-foreground">
									{area.description}
								</p>
								<Badge class="bg-gradient-to-r {area.gradient} border-0 text-white"
									>{area.badge}</Badge
								>
							</div>
						</div>
					</div>
				{/each}
			</div>
		</div>
	</section>

	<!-- Booking Tips -->
	<section class="relative bg-white py-32">
		<div class="container mx-auto px-4 sm:px-6 lg:px-8">
			<div class="mx-auto max-w-5xl">
				<div class="scroll-reveal mb-20 text-center">
					<h2 class="mb-6 text-4xl font-bold text-[color:var(--dark)] sm:text-5xl">
						<span class="text-gradient">Booking</span> Tips
					</h2>
				</div>

				<div class="grid grid-cols-1 gap-6 md:grid-cols-2">
					{#each [{ title: 'Best Time to Book', description: 'Book 3-6 months ahead for summer (June-August). Spring and fall offer better rates and you can often book 1-2 months in advance.', gradient: 'from-blue-500 to-cyan-500' }, { title: 'Room with a View', description: "Request sea-view rooms when booking. They're worth the premium for sunrise vistas over the Bay of Naples and Mount Vesuvius.", gradient: 'from-purple-500 to-pink-500' }, { title: 'Transportation', description: 'Ask about transfer services from Naples airport or train station. Many hotels offer this convenience for a reasonable fee.', gradient: 'from-green-500 to-teal-500' }, { title: 'Price Guide', description: '€ = €50-100/night, €€ = €100-200/night, €€€ = €200-400/night, €€€€ = €400+/night. Prices vary by season.', gradient: 'from-orange-500 to-red-500' }] as tip, index}
						<div class="scroll-reveal" style="transition-delay: {index * 0.1}s">
							<div class="relative h-full overflow-hidden rounded-3xl">
								<div class="absolute inset-0 bg-gradient-to-r {tip.gradient} opacity-5"></div>
								<div
									class="relative h-full rounded-3xl border-2 border-[color:var(--off-white)] bg-white p-8 transition-all duration-300 hover:border-blue-500"
								>
									<h3 class="mb-2 text-lg font-bold text-[color:var(--dark)]">{tip.title}</h3>
									<p class="text-sm leading-relaxed text-muted-foreground">{tip.description}</p>
								</div>
							</div>
						</div>
					{/each}
				</div>
			</div>
		</div>
	</section>

	<!-- CTA -->
	<section class="relative overflow-hidden py-32">
		<div
			class="animate-gradient absolute inset-0 bg-gradient-to-br from-blue-500 via-cyan-500 to-teal-500"
		></div>

		<div class="scroll-reveal relative z-10 container mx-auto px-4 text-center sm:px-6 lg:px-8">
			<div class="mx-auto max-w-3xl text-white">
				<h2 class="mb-6 text-4xl font-bold sm:text-5xl">Need Help Finding Accommodation?</h2>
				<p class="mb-10 text-xl text-white/90">
					Our WhatsApp booking service can help you find and reserve the perfect place for your stay
				</p>
				<Button
					size="lg"
					class="bg-white px-10 py-7 text-lg text-blue-600 shadow-2xl transition-all duration-500 hover:scale-105 hover:bg-[color:var(--off-white)]"
				>
					<a href="/contact" class="flex items-center space-x-2">
						<Home class="h-5 w-5" />
						<span>Contact Us for Booking Assistance</span>
					</a>
				</Button>
			</div>
		</div>
	</section>
</div>
