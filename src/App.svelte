<script>
  import FeedbackList from './components/List.svelte'
  import FeedbackStats from './components/Stats.svelte'
  import FeedbackForm from './components/Form.svelte'

  // const addFeedback = ({ detail }) => {
  //   console.log(detail)
  //   feedbacks = [{ ...detail }, ...feedbacks]
  // }
</script>

<main class="container">
  <h1>Feedback List</h1>
  <!-- <FeedbackForm on:add-feedback={addFeedback} /> -->
  <FeedbackForm />
  <FeedbackStats />
  <FeedbackList />
</main>

<style>
  h1 {
    margin-bottom: 2rem;
  }
</style>
