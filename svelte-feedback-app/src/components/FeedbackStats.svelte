<script>
  import { FeedbackStore } from '../stores';
  // export let count;
  // export let average;

  $: count = $FeedbackStore.length;
  $: average =
    $FeedbackStore.reduce((prev, { rating }) => prev + rating, 0) / $FeedbackStore.length;
</script>

<div class="feedback-stats">
  <h4>{count} Reviews</h4>
  <h4>Ratings Average: {average}</h4>
</div>

<style>
  .feedback-stats {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
</style>
