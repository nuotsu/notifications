<h1>Notifications</h1>

{#if typeof window !== 'undefined' && 'Notification' in window}
	<p>Notifications are supported</p>
{:else}
	<p>Notifications are not supported in your browser.</p>
{/if}

<script lang="ts">
</script>
