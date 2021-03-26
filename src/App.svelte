<script lang="js">
	let githubId = "";
	let repos = [];
	let result = "0 Repos";

	async function fetchRepos(githubId) {
		const url = `https://api.github.com/users/${githubId}/repos`;
		const response = await fetch(url)
		repos = await response.json();
		if (repos.length > 0) {
			repos = [...repos];
			result = `${repos.length} Repos`;
		} else {
			result = "Error";
		}
	}
</script>

<div class="uk-container">
	<div class="uk-flex uk-flex-center uk-flex-middle uk-margin">
		<div class="uk-width-2-3@m uk-card-secondary uk-card-default uk-padding-small uk-text-center">
			<div class="title"> Github Explorer</div>
			<div class="uk-text-muted uk-text-small">Fun Repos to Explore</div>
		</div>
	</div>
	<div class="uk-width-1-2@m uk-card uk-card-default uk-padding">
		<fieldset class="uk-fieldset">
			<legend class="uk-legend">Enter Github Id</legend>
			<div class="uk-margin">
				<input bind:value={githubId} class="uk-input" type="text" placeholder="Github ID">
			</div>
		</fieldset>
		<button on:click={fetchRepos(githubId)} id="add-btn" class="uk-button uk-button-default">Fetch</button>
		<div class="uk-margin">
			<legend class="uk-text-muted uk-text-small" id="result-msg"> {result} </legend>
		</div>
	</div>
	<table id="repo-table" class="uk-table uk-table-divider">
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
</div>
