<script>
  export let repos;
</script>

<table class="uk-table uk-table-divider">
  <caption> Repos :</caption>
  <thead>
    <tr>
      <th>Repo Name</th>
      <th>Description</th>
      <th>Size</th>
      <th>Languages</th>
    </tr>
  </thead>
  <tbody>
    {#each repos as repo}
      <tr>
        <td><a href=${repo.html_url}> ${repo.name} </a></td>
        <td>{repo.size}</td>
        <td>{repo.description}</td>
      </tr>
    {/each}
  </tbody>
</table>
