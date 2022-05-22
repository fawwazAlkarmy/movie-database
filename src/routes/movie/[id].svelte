<script context="module">
  /** @type {import('./__types/[slug]').Load} */
  export async function load({ fetch, params }) {
    const url = `https://api.themoviedb.org/3/movie/${params.id}?api_key=8b361ac4142c3b352faecb5b45c865ab&language=en-US`;
    const response = await fetch(url);
    const movieDetail = await response.json();
    if (response.ok) {
      return {
        props: { movieDetail },
      };
    }
    return {
      status: response.status,
      error: new Error("Error loading popular movies"),
    };
  }
</script>

<script>
  export let movieDetail;
</script>

<div class="movie-details">
  <div class="img-container">
    <img
      src={"https://image.tmdb.org/t/p/original" + movieDetail.backdrop_path}
      alt={movieDetail.title}
    />
  </div>
  <div class="txt-container">
    <h1>{movieDetail.title}</h1>
    <p class="overview">{movieDetail.overview}</p>
    <p>
      <span>Release Date:</span>
      {movieDetail.release_date} <br />
      <span>Budget:</span> ${movieDetail.budget} <br />
      <span>Rating:</span>
      {movieDetail.vote_average} <br />
      <span>Runtime:</span>
      {movieDetail.runtime} minutes <br />
    </p>
  </div>
</div>

<style>
  h1 {
    padding: 1rem 0 1rem;
  }
  p {
    padding: 1rem 0;
  }
  .img-container {
    width: 100%;
  }
  img {
    width: 100%;
    border-radius: 1rem;
  }
  .movie-details {
    margin: 2rem 20%;
  }
  span {
    font-weight: bold;
  }
</style>
