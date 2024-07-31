<h1>Notifications</h1>

{#if typeof window !== 'undefined' && 'Notification' in window}
	{#await Notification.requestPermission()}
		<p>Requesting permission to send notifications</p>
	{:then permission}
		{#if permission === 'granted'}
			<button
				on:click={() => {
					new Notification('Hello world!')
				}}
			>
				Notify
			</button>
		{:else}
			<p>Notifications are disabled</p>
		{/if}
	{/await}
{:else}
	<p>Notifications are not supported in your browser.</p>
{/if}

<script lang="ts">
</script>
