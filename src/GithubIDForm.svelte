<script>
  export let fetchRepos;
  let githubId;
</script>

<div class="uk-width-1-2@m uk-card uk-card-default uk-padding">
  <fieldset class="uk-fieldset">
    <legend class="uk-legend">Enter todo item</legend>
    <div class="uk-margin">
      <input bind:value={githubId} class="uk-input" placeholder="Todo">
    </div>
  </fieldset>
  <button on:click={fetchRepos(githubId)} class="uk-button uk-button-default">Add Todo</button>
</div>
