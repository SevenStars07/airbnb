<script lang='ts'>
	// The ordering of these imports is critical to your app working properly
	import '@skeletonlabs/skeleton/themes/theme-rocket.css';
	// If you have source.organizeImports set to true in VSCode, then it will auto change this ordering
	import '@skeletonlabs/skeleton/styles/all.css';
	// Most of your app wide CSS should be put in this file
	import { page } from '$app/stores';
	import { AppBar, AppRail, AppRailTile, AppShell } from '@skeletonlabs/skeleton';
	import { writable, type Writable } from 'svelte/store';
	import '../app.postcss';
	import Icon from '../components/Icon.svelte';

	const storeValue: Writable<number> = writable(0);
</script>

<svelte:head>
<link href="https://fonts.cdnfonts.com/css/space-grotesk" rel="stylesheet">
</svelte:head>
<!-- App Shell -->
<AppShell slotSidebarLeft="dark bg-surface-100-800-token">
	<svelte:fragment slot="header">
		<!-- App Bar -->
		<AppBar>
			<svelte:fragment slot="lead">
				<strong class="text-xl uppercase">RentBNB</strong>
			</svelte:fragment>
			<svelte:fragment slot="trail">
				<a
					class="btn btn-sm variant-ghost-surface"
					href="https://twitter.com/SkeletonUI"
					target="_blank"
					rel="noreferrer"
				>
					Login
				</a>
				<a
					class="btn btn-sm variant-ghost-surface"
					href="https://github.com/skeletonlabs/skeleton"
					target="_blank"
					rel="noreferrer"
				>
					My account
				</a>
			</svelte:fragment>
		</AppBar>
	</svelte:fragment>
	<svelte:fragment slot="sidebarLeft">
		<AppRail selected={storeValue}>
			<AppRailTile tag="a" label="Home" href="/" class="{"/" === $page.url.pathname ? 'bg-primary-500' : ''}">
				<Icon name="house" class="fill-current" />
			</AppRailTile>
			<AppRailTile tag="a" label="Properties" href="/properties" class="{"/properties" === $page.url.pathname ? 'bg-primary-500' : ''}">
				<Icon name="hotel" class="fill-current" />
			</AppRailTile>
			<AppRailTile tag="a" label="Bookings" href="/bookings" class="{"/bookings" === $page.url.pathname ? 'bg-primary-500' : ''}">
				<Icon name="beach-house" class="fill-current stroke-current" />
			</AppRailTile>
			<AppRailTile tag="a" label="Settings" href="/settings" class="{"/settings" === $page.url.pathname ? 'bg-primary-500' : ''}">
				<Icon name="settings" class="fill-current stroke-current" />
			</AppRailTile>
		</AppRail>
	</svelte:fragment>
	<!-- Page Route Content -->
	<slot />
</AppShell>
