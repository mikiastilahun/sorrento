<script lang="ts">
	import { page } from '$app/stores';
	import Button from '$lib/components/ui/button/button.svelte';
	import { Menu, X, ChevronDown, Sparkles } from '@lucide/svelte';
	import { onMount } from 'svelte';

	let mobileMenuOpen = $state(false);
	let scrolled = $state(false);
	let hidden = $state(false);
	let lastScroll = $state(0);

	// Advanced scroll handling with hide/show on scroll
	onMount(() => {
		const handleScroll = () => {
			const currentScroll = window.scrollY;
			scrolled = currentScroll > 50;

			// Hide navbar on scroll down, show on scroll up
			if (currentScroll > lastScroll && currentScroll > 100) {
				hidden = true;
			} else {
				hidden = false;
			}
			lastScroll = currentScroll;
		};

		window.addEventListener('scroll', handleScroll);
		return () => window.removeEventListener('scroll', handleScroll);
	});

	const navLinks = [
		{ name: 'Home', href: '/' },
		{
			name: 'Sorrento',
			href: '/sorrento',
			submenu: [
				{ name: 'Eat', href: '/sorrento/eat' },
				{ name: 'Stay', href: '/sorrento/stay' },
				{ name: 'Do', href: '/sorrento/do' }
			]
		},
		{
			name: 'Surrounding',
			href: '/surrounding',
			submenu: [
				{ name: 'Capri', href: '/surrounding/capri' },
				{ name: 'Amalfi Coast', href: '/surrounding/amalfi' },
				{ name: 'Naples', href: '/surrounding/naples' },
				{ name: 'Procida', href: '/surrounding/procida' },
				{ name: 'Ischia', href: '/surrounding/ischia' },
				{ name: 'Salerno', href: '/surrounding/salerno' }
			]
		},
		{ name: 'Blog', href: '/blog' },
		{ name: 'About', href: '/about' },
		{ name: 'Contact', href: '/contact' }
	];
</script>

<nav
	class="fixed top-0 right-0 left-0 z-50 transition-all duration-500 ease-out {hidden
		? '-translate-y-full'
		: 'translate-y-0'} {scrolled ? 'py-2' : 'py-4'}"
>
	<div class="container mx-auto px-4 sm:px-6 lg:px-8">
		<div
			class="rounded-2xl {scrolled
				? 'glass-dark shadow-2xl'
				: 'glass-dark shadow-lg'} transition-all duration-500"
		>
			<div class="flex items-center justify-between px-6 py-4">
				<!-- Logo with gradient -->
				<a href="/" class="group relative flex items-center space-x-2">
					<div
						class="absolute -inset-2 rounded-xl bg-gradient-to-r from-[color:var(--purple-lavender)] to-[color:var(--turquoise)] opacity-0 blur-xl transition-all duration-500 group-hover:opacity-20"
					></div>
					<Sparkles class="relative h-6 w-6 animate-pulse text-[color:var(--turquoise)]" />
					<div class="relative text-xl font-bold sm:text-2xl">
						<span class="text-gradient">Welcome</span><span class="text-[color:var(--turquoise)]"
							>2</span
						><span class="text-gradient">Sorrento</span>
					</div>
				</a>

				<!-- Desktop Navigation -->
				<div class="hidden items-center space-x-1 lg:flex">
					{#each navLinks as link}
						{#if link.submenu}
							{@const isActive = $page.url.pathname.startsWith(link.href)}
							<div class="group relative">
								<a
									href={link.href}
									class="group flex items-center space-x-1 rounded-xl px-4 py-2 font-medium text-white/90 transition-all duration-300 hover:bg-white/10 hover:text-white {isActive
										? 'bg-white/10'
										: ''}"
								>
									<span>{link.name}</span>
									<ChevronDown
										class="h-4 w-4 transition-transform duration-300 group-hover:rotate-180"
									/>
									{#if isActive}
										<div
											class="absolute bottom-0 left-1/2 h-0.5 w-1/2 -translate-x-1/2 rounded-full bg-gradient-to-r from-[color:var(--purple-lavender)] to-[color:var(--turquoise)]"
										></div>
									{/if}
								</a>
								<div
									class="invisible absolute top-full left-0 mt-2 w-56 translate-y-2 opacity-0 transition-all duration-300 group-hover:visible group-hover:translate-y-0 group-hover:opacity-100"
								>
									<div
										class="glass-dark overflow-hidden rounded-2xl border border-white/10 p-2 shadow-2xl"
									>
										{#each link.submenu as sublink}
											<a
												href={sublink.href}
												class="block rounded-xl px-4 py-3 text-sm text-white/80 transition-all duration-200 hover:bg-white/10 hover:text-white {$page
													.url.pathname === sublink.href
													? 'bg-gradient-to-r from-[color:var(--purple-lavender)] to-[color:var(--turquoise)] font-semibold text-white'
													: ''}"
											>
												{sublink.name}
											</a>
										{/each}
									</div>
								</div>
							</div>
						{:else}
							<a
								href={link.href}
								class="group relative overflow-hidden rounded-xl px-4 py-2 font-medium text-white/90 transition-all duration-300 hover:bg-white/10 hover:text-white {$page
									.url.pathname === link.href
									? 'bg-white/10'
									: ''}"
							>
								<span class="relative z-10">{link.name}</span>
								{#if $page.url.pathname === link.href}
									<div
										class="absolute bottom-0 left-1/2 h-0.5 w-1/2 -translate-x-1/2 rounded-full bg-gradient-to-r from-[color:var(--purple-lavender)] to-[color:var(--turquoise)]"
									></div>
								{/if}
							</a>
						{/if}
					{/each}

					<!-- CTA Button -->
					<a href="/contact" class="ml-4">
						<Button
							class="bg-gradient-to-r from-[color:var(--purple-lavender)] to-[color:var(--turquoise)] transition-all duration-300 hover:scale-105 hover:shadow-lg hover:shadow-[color:var(--purple-lavender)]/50"
						>
							<div class="flex items-center space-x-2">
								<Sparkles class="h-4 w-4" />
								<span>Get in Touch</span>
							</div>
						</Button>
					</a>
				</div>

				<!-- Mobile Menu Button -->
				<button
					onclick={() => (mobileMenuOpen = !mobileMenuOpen)}
					class="group relative rounded-xl p-2 text-white transition-all duration-300 hover:bg-white/10 lg:hidden"
					aria-label="Toggle menu"
				>
					<div
						class="absolute inset-0 rounded-xl bg-gradient-to-r from-[color:var(--purple-lavender)] to-[color:var(--turquoise)] opacity-0 blur transition-all duration-300 group-hover:opacity-20"
					></div>
					{#if mobileMenuOpen}
						<X class="relative h-6 w-6" />
					{:else}
						<Menu class="relative h-6 w-6" />
					{/if}
				</button>
			</div>
		</div>
	</div>

	<!-- Mobile Menu -->
	{#if mobileMenuOpen}
		<div class="animate-fade-in mt-4 lg:hidden">
			<div class="container mx-auto px-4">
				<div class="glass-dark overflow-hidden rounded-2xl border border-white/10 p-4 shadow-2xl">
					<div class="space-y-1">
						{#each navLinks as link}
							{#if link.submenu}
								<div class="space-y-1">
									<a
										href={link.href}
										class="block rounded-xl px-4 py-3 font-medium text-white/90 transition-all duration-200 hover:bg-white/10 hover:text-white"
									>
										{link.name}
									</a>
									<div class="space-y-1 pl-4">
										{#each link.submenu as sublink}
											<a
												href={sublink.href}
												class="block rounded-xl px-4 py-2 text-sm text-white/70 transition-all duration-200 hover:bg-white/10 hover:text-white {$page
													.url.pathname === sublink.href
													? 'bg-gradient-to-r from-[color:var(--purple-lavender)] to-[color:var(--turquoise)] font-semibold text-white'
													: ''}"
												onclick={() => (mobileMenuOpen = false)}
											>
												{sublink.name}
											</a>
										{/each}
									</div>
								</div>
							{:else}
								<a
									href={link.href}
									class="block rounded-xl px-4 py-3 font-medium text-white/90 transition-all duration-200 hover:bg-white/10 hover:text-white {$page
										.url.pathname === link.href
										? 'bg-white/10'
										: ''}"
									onclick={() => (mobileMenuOpen = false)}
								>
									{link.name}
								</a>
							{/if}
						{/each}

						<div class="border-t border-white/10 pt-4">
							<a href="/contact" class="block" onclick={() => (mobileMenuOpen = false)}>
								<Button
									class="w-full bg-gradient-to-r from-[color:var(--purple-lavender)] to-[color:var(--turquoise)] transition-all duration-300 hover:shadow-lg"
								>
									<div class="flex w-full items-center justify-center space-x-2">
										<Sparkles class="h-4 w-4" />
										<span>Get in Touch</span>
									</div>
								</Button>
							</a>
						</div>
					</div>
				</div>
			</div>
		</div>
	{/if}
</nav>

<!-- Spacer to prevent content from going under fixed nav -->
<div class="h-24"></div>
