<script>
  import FeedbackStats from './components/FeedbackStats.svelte';
  import FeedbackList from './components/FeedbackList.svelte';
  import FeedbackForm from './components/FeedbackForm.svelte';

  // $: count = feedback.length;
  // $: average = feedback.reduce((prev, { rating }) => prev + rating, 0) / feedback.length;

  // const deleteFeedback = (e) => {
  //   const itemId = e.detail;
  //   feedback = feedback.filter((item) => item.id != itemId);
  // };

  // const addFeedback = (e) => {
  //   const newFeedback = e.detail;
  //   feedback = [newFeedback, ...feedback];
  // };
</script>

<main class="container">
  <!-- <FeedbackForm on:add-feedback={addFeedback} /> -->
  <FeedbackForm />
  <!-- <FeedbackStats {count} {average} /> -->
  <FeedbackStats />
  <!-- <FeedbackList on:delete-feedback={deleteFeedback} /> -->
  <FeedbackList />
</main>

<style>
</style>
