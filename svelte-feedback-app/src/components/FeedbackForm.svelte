<script>
  import { v4 as uuidV4 } from 'uuid';
  //   import { createEventDispatcher } from 'svelte';

  import { FeedbackStore } from '../stores';
  import Card from './Card.svelte';
  import Button from './Button.svelte';
  import RatingSelect from './RatingSelect.svelte';

  //   const dispatch = createEventDispatcher();

  let text = '';
  let rating = 10;
  let btnDisabled = true;
  let message;

  const handleInput = () => {
    if (text.trim().length <= 10) {
      message = 'Text must be at least 10 characters';
      btnDisabled = true;
    } else {
      message = null;
      btnDisabled = false;
    }
  };

  const handleSelect = (e) => {
    rating = e.detail;
  };

  const handleSubmit = () => {
    //just to make sure people arent modifying in dev tools
    if (text.trim().length > 10) {
      const newFeedback = {
        id: uuidV4(),
        text,
        rating: +rating,
      };
      //   dispatch('add-feedback', newFeedback);
      FeedbackStore.update((currentFeedback) => {
        return [newFeedback, ...currentFeedback];
      });
      text = '';
    }
  };
</script>

<Card>
  <header>
    <h2>How would you rate your service with us?</h2>
  </header>
  <form on:submit|preventDefault={handleSubmit}>
    <RatingSelect on:rating-select={handleSelect} />
    <div class="input-group">
      <input
        type="text"
        placeholder="Tell us something that keeps you coming back"
        on:input={handleInput}
        bind:value={text}
      />
      <Button type="submit" disabled={btnDisabled}>Send</Button>
    </div>
    {#if message}
      <div class="message">
        {message}
      </div>
    {/if}
  </form>
</Card>

<style>
  header {
    max-width: 400px;
    margin: auto;
  }

  header h2 {
    font-size: 22px;
    font-weight: 600;
    text-align: center;
  }

  .input-group {
    display: flex;
    flex-direction: row;
    border: 1px solid #ccc;
    padding: 8px 10px;
    border-radius: 8px;
    margin-top: 15px;
  }

  input {
    flex-grow: 2;
    border: none;
    font-size: 16px;
  }

  input:focus {
    outline: none;
  }

  .message {
    padding-top: 10px;
    text-align: center;
    color: rebeccapurple;
  }
</style>
