<h1><a href="/">Notifications</a></h1>

{#if typeof window !== 'undefined' && 'Notification' in window}
	{#await requestPermission()}
		<p>Requesting permission to send notifications...</p>
	{:then}
		{#if permission === 'granted'}
			<p>Notifications are enabled.</p>
			<button
				onclick={() => {
					new Notification('Hello world!')
				}}
			>
				Send notification
			</button>
		{:else}
			<p>Notifications are disabled.</p>
			<button onclick={requestPermission}>Enable notifications</button>
		{/if}
	{/await}
{:else}
	<p>Notifications are not supported in your browser.</p>
{/if}

<script lang="ts">
	let permission = $state<NotificationPermission>('default')

	async function requestPermission() {
		const result = await Notification.requestPermission()
		permission = result
	}
</script>
