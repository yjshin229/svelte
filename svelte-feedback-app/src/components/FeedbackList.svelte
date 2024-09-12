<script>
  import { scale, fade } from 'svelte/transition';
  // import { onDestroy, onMount } from 'svelte';

  import { FeedbackStore } from '../stores';
  import FeedbackItem from './FeedbackItem.svelte';
  // let feedback = [];

  // //calling subscribe returns a function for unsubscribe
  // const unsubscribe = FeedbackStore.subscribe((data) => (feedback = data));

  // onMount(() => {});

  // onDestroy(() => {
  //   unsubscribe();
  // });
</script>

<!-- will bring from store and unsubscribe automatically if using $FeedbackStore -->
{#each $FeedbackStore as fb (fb.id)}
  <div in:scale={{ duration: 500 }} out:fade={{ duration: 500 }}>
    <!-- <FeedbackItem item={fb} on:delete-feedback /> -->
    <FeedbackItem item={fb} />
  </div>
{/each}
