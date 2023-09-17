<script>
  import { MetaMaskStore } from "$lib";
  import { onMount } from "svelte";

  const { walletState, isMetaMaskPresent, connect, loaded, init } =
    MetaMaskStore();

  onMount(() => {
    init();
  });
</script>

<h1>Welcome to SvelteKit</h1>

{#if $loaded}
  {#if $isMetaMaskPresent}
    {#if Boolean($walletState.account)}
      <p>{$walletState.account}</p>
    {:else}
      <button on:click={connect}>Connect Wallet</button>
    {/if}
  {:else}
    <p>Please install MetaMask</p>
  {/if}
{:else}
  <p>Loading...</p>
{/if}
