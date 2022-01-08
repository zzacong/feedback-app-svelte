<script>
  import { FeedbackStore } from '../stores'
  import Card from './Card.svelte'

  export let feedback = {}

  const handleDelete = id => {
    FeedbackStore.update(data => data.filter(fb => fb.id !== id))
  }
</script>

<Card>
  <div class="num-display">
    {feedback.rating}
  </div>
  <button class="close" on:click={() => handleDelete(feedback.id)}>X</button>
  <p class="text-display">{feedback.text}</p>
</Card>

<style>
  .num-display {
    position: absolute;
    top: -10px;
    left: -10px;
    width: 50px;
    height: 50px;
    background: #ff6a95;
    color: #fff;
    border: 1px #eee solid;
    border-radius: 50%;
    padding: 10px;
    text-align: center;
    font-size: 19px;
  }

  .close {
    position: absolute;
    top: 0.8rem;
    right: 1.2rem;
    cursor: pointer;
    background: none;
    border: none;
  }
</style>
