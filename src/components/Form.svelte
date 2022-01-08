<script>
  import { FeedbackStore } from '../stores'
  import Card from './Card.svelte'
  import Button from './Button.svelte'
  import RatingSelect from './RatingSelect.svelte'

  let text = ''
  let btnDisabled = true
  let rating = 10
  let min = 10
  let message

  const handleInput = () => {
    if (text.trim().length < min) {
      message = `Text must be at least ${min} characters`
      btnDisabled = true
      return
    }
    message = null
    btnDisabled = false
  }

  const handleSelect = e => (rating = e.detail)

  const handleSubmit = () => {
    if (text.trim().length < min) return

    const newFeedback = {
      text,
      id: (Math.random() * 3000).toFixed(0),
      rating: rating,
    }
    FeedbackStore.update(data => [{ ...newFeedback }, ...data])
    text = ''
  }
</script>

<Card>
  <header><h2>How would you rate your service with us?</h2></header>

  <form on:submit|preventDefault={handleSubmit}>
    <RatingSelect on:rating-select={handleSelect} {rating} />
    <div class="input-group">
      <input
        type="text"
        placeholder="Tell us something that you like"
        bind:value={text}
        on:input={handleInput}
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
