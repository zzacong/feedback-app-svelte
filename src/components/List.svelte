<script>
  // import { onDestroy } from 'svelte'
  import { fade, scale } from 'svelte/transition'
  import { FeedbackStore } from '../stores'
  import FeedbackItem from './Item.svelte'

  // let feedbacks
  // const unsubscribe = FeedbackStore.subscribe(data => (feedbacks = data))
  // onDestroy(() => unsubscribe())
</script>

<!-- {#each feedbacks as fb (fb.id)} -->
{#each $FeedbackStore as fb (fb.id)}
  <div in:scale out:fade>
    <FeedbackItem feedback={fb} />
  </div>
{/each}
