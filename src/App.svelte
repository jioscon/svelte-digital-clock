<script>
  import { onDestroy } from 'svelte';

  let now = new Date();
  $: hours = now.getHours();
  $: minutes = now.getMinutes();
  $: seconds = now.getSeconds();

  const interval = setInterval( () => now = new Date(), 1000 );

  onDestroy(() => {
    clearInterval(interval);
  });
</script>

<span>{hours < 12 ? 'AM' : 'PM'} {hours} : </span>
<span>{minutes < 10 ? 0 : ''}{minutes} : </span>
<span>{seconds < 10 ? 0 : ''}{seconds}</span>