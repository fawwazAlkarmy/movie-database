<script context="module">
  /** @type {import('./__types/[slug]').Load} */
  export async function load({ fetch }) {
    const url =
      "https://api.themoviedb.org/3/movie/popular?api_key=8b361ac4142c3b352faecb5b45c865ab&language=en-US&page=1";
    const response = await fetch(url);
    const popular = await response.json();
    if (response.ok) {
      return {
        props: { popular: popular.results },
      };
    }
    return {
      status: response.status,
      error: new Error("Error loading popular movies"),
    };
  }
</script>

<script>
  import PopularMovies from "../components/PopularMovies.svelte";
  import SearchMovies from "../components/SearchMovies.svelte";
  export let popular;
</script>

<div class="index">
  <SearchMovies />
  <PopularMovies {popular} />
</div>
