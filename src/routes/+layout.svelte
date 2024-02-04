<script>
	import '../app.postcss';
	import { AppShell, AppBar } from '@skeletonlabs/skeleton';
</script>

<svelte:head>
	<!-- 	<style>
		#appShell {
			background-image:
				radial-gradient(at 71% 77%,var(--color-primary-50) 0,transparent 21%), radial-gradient(
					at 71% 77%,
					var(--color-primary-50) 100%,
					transparent 21%
				),
				radial-gradient(at 36% 47%, var(--color-primary-500) 0, transparent 50%),
				radial-gradient(at 54% 29%, var(--color-primary-500) 0, transparent 28%),
				radial-gradient(at 45% 51%, var(--color-primary-50) 0, transparent 53%),
				radial-gradient(at 73% 44%, var(--tw-color-gradient-2) 0, transparent 54%),
				radial-gradient(at 24% 7%, var(--tw-color-gradient-2) 0, transparent 40%),
				radial-gradient(at 76% 46%, var(--color-primary-50) 0, transparent 50%);
		}
	</style>
 --></svelte:head
>
<!-- App Shell -->
<AppShell>
	<svelte:fragment slot="header">
		<!-- App Bar -->
		<AppBar>
			<svelte:fragment slot="lead">
				<img class="object-contain h-20 w-96 mb-2" src="coculator.png" alt="" />
			</svelte:fragment>
			<svelte:fragment slot="trail">
				<a
					class="btn btn-sm variant-ghost-surface"
					href="https://discord.gg/EXqV7W8MtY"
					target="_blank"
					rel="noreferrer"
				>
					Discord
				</a>
				<a
					class="btn btn-sm variant-ghost-surface"
					href="https://twitter.com/SkeletonUI"
					target="_blank"
					rel="noreferrer"
				>
					Twitter
				</a>
				<a
					class="btn btn-sm variant-ghost-surface"
					href="https://github.com/skeletonlabs/skeleton"
					target="_blank"
					rel="noreferrer"
				>
					GitHub
				</a>
			</svelte:fragment>
		</AppBar>
	</svelte:fragment>
	<!-- Page Route Content -->
	<slot />
</AppShell>
