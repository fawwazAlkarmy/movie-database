<script context="module">
  /** @type {import('./__types/[slug]').Load} */
  export async function load({ fetch, params }) {
    const url = `https://api.themoviedb.org/3/search/multi?api_key=8b361ac4142c3b352faecb5b45c865ab&language=en-US&query=${params.id}&page=1&include_adult=false`;
    const response = await fetch(url);
    const searchedMovie = await response.json();
    console.log(searchedMovie);
    if (response.ok) {
      return {
        props: { searchedMovie: searchedMovie.results },
      };
    }
    return {
      status: response.status,
      error: new Error("Error loading popular movies"),
    };
  }
</script>

<script>
  import MovieCard from "../../components/MovieCard.svelte";
  export let searchedMovie;
</script>

<div class="searched-movies">
  {#each searchedMovie as movie}
    <MovieCard {movie} />
  {/each}
</div>

<style>
  .searched-movies {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    grid-column-gap: 1rem;
    grid-row-gap: 2rem;
  }
</style>
