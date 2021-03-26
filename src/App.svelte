<script lang="js">
	import Title from "./Title.svelte"
	import GithubIDForm from "./GithubIDForm.svelte";
	import RepoList from "./RepoList.svelte";

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
	<Title title="Github Explorer" subTitle="Fun Repos to Exlore"/>
  <GithubIDForm {fetchRepos}/>
  <RepoList {repos}/>
</div>
