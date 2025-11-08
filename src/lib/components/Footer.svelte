<script lang="ts">
	import {
		Facebook,
		Instagram,
		Twitter,
		Mail,
		Phone,
		MapPin,
		Clock,
		Sparkles,
		Heart,
		ExternalLink
	} from '@lucide/svelte';
	import { onMount } from 'svelte';

	let currentYear = new Date().getFullYear();
	let email = $state('');

	const quickLinks = [
		{ name: 'Home', href: '/' },
		{ name: 'Sorrento Guide', href: '/sorrento' },
		{ name: 'Destinations', href: '/surrounding' },
		{ name: 'Blog', href: '/blog' },
		{ name: 'About Us', href: '/about' }
	];

	const services = [
		{ name: 'WhatsApp Booking', href: '/about#services' },
		{ name: 'Accommodations', href: '/sorrento/stay' },
		{ name: 'Restaurants', href: '/sorrento/eat' },
		{ name: 'Activities', href: '/sorrento/do' },
		{ name: 'Contact Us', href: '/contact' }
	];

	const destinations = [
		{ name: 'Capri Island', href: '/surrounding/capri' },
		{ name: 'Amalfi Coast', href: '/surrounding/amalfi' },
		{ name: 'Naples', href: '/surrounding/naples' },
		{ name: 'Procida', href: '/surrounding/procida' },
		{ name: 'Ischia', href: '/surrounding/ischia' }
	];

	function handleQuickSubscribe(e: Event) {
		e.preventDefault();
		console.log('Quick subscribe:', email);
		email = '';
	}
</script>

<footer class="relative overflow-hidden">
	<!-- Animated Background -->
	<div
		class="animate-gradient absolute inset-0 bg-gradient-to-br from-[color:var(--dark)] via-[color:var(--deep-purple)] to-[color:var(--dark)]"
	></div>

	<!-- Decorative Elements -->
	<div
		class="absolute top-0 left-0 h-96 w-96 -translate-x-1/2 -translate-y-1/2 rounded-full bg-[color:var(--purple-lavender)] opacity-10 blur-3xl"
	></div>
	<div
		class="absolute right-0 bottom-0 h-96 w-96 translate-x-1/2 translate-y-1/2 rounded-full bg-[color:var(--turquoise)] opacity-10 blur-3xl"
	></div>

	<div class="relative z-10">
		<!-- Main Footer Content -->
		<div class="container mx-auto px-4 py-16 sm:px-6 lg:px-8">
			<div class="mb-16 grid grid-cols-1 gap-12 md:grid-cols-2 lg:grid-cols-12">
				<!-- Brand Section (Larger) -->
				<div class="space-y-6 lg:col-span-5">
					<div class="group flex items-center space-x-3">
						<Sparkles class="h-8 w-8 animate-pulse text-[color:var(--turquoise)]" />
						<h3 class="text-3xl font-bold">
							<span class="text-gradient">Welcome</span><span class="text-[color:var(--turquoise)]"
								>2</span
							><span class="text-gradient">Sorrento</span>
						</h3>
					</div>
					<p class="max-w-md text-lg leading-relaxed text-white/70">
						Your ultimate guide to discovering the magic of Sorrento and the breathtaking Amalfi
						Coast. Created with passion by locals who know every hidden gem.
					</p>

					<!-- Contact Info Cards -->
					<div class="space-y-3">
						<a
							href="mailto:margheroba@email.com"
							class="glass group flex items-center space-x-3 rounded-xl border border-white/10 p-4 transition-all duration-300 hover:bg-white/10"
						>
							<div
								class="flex h-10 w-10 items-center justify-center rounded-lg bg-gradient-to-br from-[color:var(--purple-lavender)] to-[color:var(--turquoise)] transition-transform group-hover:scale-110"
							>
								<Mail class="h-5 w-5 text-white" />
							</div>
							<div class="flex-1">
								<div class="mb-0.5 text-xs text-white/50">Email Us</div>
								<div class="font-medium text-white/90">margheroba@email.com</div>
							</div>
							<ExternalLink
								class="h-4 w-4 text-white/50 transition-colors group-hover:text-white/90"
							/>
						</a>

						<a
							href="tel:+39123456789"
							class="glass group flex items-center space-x-3 rounded-xl border border-white/10 p-4 transition-all duration-300 hover:bg-white/10"
						>
							<div
								class="flex h-10 w-10 items-center justify-center rounded-lg bg-gradient-to-br from-[color:var(--turquoise)] to-[color:var(--light-turquoise)] transition-transform group-hover:scale-110"
							>
								<Phone class="h-5 w-5 text-white" />
							</div>
							<div class="flex-1">
								<div class="mb-0.5 text-xs text-white/50">WhatsApp</div>
								<div class="font-medium text-white/90">Available 24/7</div>
							</div>
							<ExternalLink
								class="h-4 w-4 text-white/50 transition-colors group-hover:text-white/90"
							/>
						</a>
					</div>

					<!-- Social Links -->
					<div class="flex space-x-3 pt-4">
						<button
							type="button"
							class="glass group flex h-12 w-12 items-center justify-center rounded-xl border border-white/10 transition-all duration-300 hover:scale-110 hover:bg-white/10"
							aria-label="Facebook"
						>
							<Facebook class="h-5 w-5 text-white/70 transition-colors group-hover:text-white" />
						</button>
						<button
							type="button"
							class="glass group flex h-12 w-12 items-center justify-center rounded-xl border border-white/10 transition-all duration-300 hover:scale-110 hover:bg-white/10"
							aria-label="Instagram"
						>
							<Instagram class="h-5 w-5 text-white/70 transition-colors group-hover:text-white" />
						</button>
						<button
							type="button"
							class="glass group flex h-12 w-12 items-center justify-center rounded-xl border border-white/10 transition-all duration-300 hover:scale-110 hover:bg-white/10"
							aria-label="Twitter"
						>
							<Twitter class="h-5 w-5 text-white/70 transition-colors group-hover:text-white" />
						</button>
					</div>
				</div>

				<!-- Quick Links -->
				<div class="space-y-6 lg:col-span-2">
					<h4 class="flex items-center space-x-2 text-lg font-bold text-white">
						<div
							class="h-6 w-1 rounded-full bg-gradient-to-b from-[color:var(--purple-lavender)] to-[color:var(--turquoise)]"
						></div>
						<span>Quick Links</span>
					</h4>
					<ul class="space-y-3">
						{#each quickLinks as link}
							<li>
								<a
									href={link.href}
									class="group flex items-center space-x-2 text-white/70 transition-all duration-300 hover:translate-x-2 hover:text-white"
								>
									<div
										class="h-1 w-1 rounded-full bg-[color:var(--turquoise)] opacity-0 transition-opacity group-hover:opacity-100"
									></div>
									<span>{link.name}</span>
								</a>
							</li>
						{/each}
					</ul>
				</div>

				<!-- Our Services -->
				<div class="space-y-6 lg:col-span-2">
					<h4 class="flex items-center space-x-2 text-lg font-bold text-white">
						<div
							class="h-6 w-1 rounded-full bg-gradient-to-b from-[color:var(--turquoise)] to-[color:var(--light-turquoise)]"
						></div>
						<span>Our Services</span>
					</h4>
					<ul class="space-y-3">
						{#each services as service}
							<li>
								<a
									href={service.href}
									class="group flex items-center space-x-2 text-white/70 transition-all duration-300 hover:translate-x-2 hover:text-white"
								>
									<div
										class="h-1 w-1 rounded-full bg-[color:var(--purple-lavender)] opacity-0 transition-opacity group-hover:opacity-100"
									></div>
									<span>{service.name}</span>
								</a>
							</li>
						{/each}
					</ul>
				</div>

				<!-- Popular Destinations -->
				<div class="space-y-6 lg:col-span-3">
					<h4 class="flex items-center space-x-2 text-lg font-bold text-white">
						<div
							class="h-6 w-1 rounded-full bg-gradient-to-b from-[color:var(--turquoise)] to-[color:var(--purple-lavender)]"
						></div>
						<span>Top Destinations</span>
					</h4>
					<ul class="space-y-3">
						{#each destinations as dest}
							<li>
								<a
									href={dest.href}
									class="group flex items-center space-x-2 text-white/70 transition-all duration-300 hover:translate-x-2 hover:text-white"
								>
									<MapPin
										class="h-3 w-3 text-[color:var(--turquoise)] opacity-50 transition-opacity group-hover:opacity-100"
									/>
									<span>{dest.name}</span>
								</a>
							</li>
						{/each}
					</ul>

					<!-- Quick Subscribe -->
					<div class="pt-6">
						<form onsubmit={handleQuickSubscribe} class="space-y-3">
							<div class="relative">
								<input
									type="email"
									placeholder="Quick subscribe"
									bind:value={email}
									required
									class="h-11 w-full rounded-xl border border-white/10 bg-white/5 px-4 pr-11 text-white transition-all outline-none placeholder:text-white/40 focus:border-white/30 focus:bg-white/10"
								/>
								<button
									type="submit"
									class="absolute top-1 right-1 bottom-1 rounded-lg bg-gradient-to-r from-[color:var(--purple-lavender)] to-[color:var(--turquoise)] px-3 transition-transform hover:scale-105"
								>
									<Mail class="h-4 w-4 text-white" />
								</button>
							</div>
						</form>
					</div>
				</div>
			</div>

			<!-- Divider -->
			<div class="mb-8 h-px bg-gradient-to-r from-transparent via-white/20 to-transparent"></div>

			<!-- Bottom Bar -->
			<div class="flex flex-col items-center justify-between space-y-4 md:flex-row md:space-y-0">
				<div class="flex items-center space-x-2 text-sm text-white/60">
					<span>© {currentYear} Welcome2Sorrento.</span>
					<span class="hidden sm:inline">Made with</span>
					<Heart
						class="h-4 w-4 animate-pulse fill-[color:var(--turquoise)] text-[color:var(--turquoise)]"
					/>
					<span class="hidden sm:inline">in Italy</span>
				</div>

				<div class="flex items-center space-x-6">
					<a
						href="/privacy"
						class="text-sm text-white/60 transition-colors duration-200 hover:text-white"
					>
						Privacy Policy
					</a>
					<div class="h-1 w-1 rounded-full bg-white/30"></div>
					<a
						href="/terms"
						class="text-sm text-white/60 transition-colors duration-200 hover:text-white"
					>
						Terms of Service
					</a>
					<div class="h-1 w-1 rounded-full bg-white/30"></div>
					<a
						href="/contact"
						class="text-sm text-white/60 transition-colors duration-200 hover:text-white"
					>
						Contact
					</a>
				</div>
			</div>
		</div>

		<!-- Bottom Accent -->
		<div
			class="animate-gradient h-1 bg-gradient-to-r from-[color:var(--purple-lavender)] via-[color:var(--turquoise)] to-[color:var(--purple-lavender)]"
		></div>
	</div>
</footer>
