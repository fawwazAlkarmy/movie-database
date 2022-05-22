<script>
  let inputValue = "";
  import { goto } from "$app/navigation";
  function submitSearch() {
    goto("/search/" + inputValue);
  }
</script>

<form class="search" on:submit|preventDefault={submitSearch}>
  <input
    bind:value={inputValue}
    type="text"
    name="search_movies"
    placeholder="Search Movies"
  />
  <button>Search</button>
</form>

<style>
  .search {
    position: relative;
    width: 30%;
    margin: 1rem;
  }
  button {
    font-size: 0.7rem;
    padding: 0 1rem;
    background: rgb(96, 110, 201);
    color: #fff;
    font-weight: bold;
    border: none;
    border-top-right-radius: 10px;
    border-bottom-right-radius: 10px;
    cursor: pointer;
    transform: translate(0, 50%);
    position: absolute;
    right: 0;
    bottom: 50%;
    height: 100%;
  }
  input {
    width: 100%;
    border: none;
    font-size: 1rem;
    padding: 0.5rem 1rem;
    font-family: "Poppins";
    color: rgb(255, 255, 255);
    transition: background 0.3s ease-in-out;
    font-weight: bold;
    background: rgb(63, 63, 63);
    border-radius: 10px;
    outline: none;
    padding: 1rem;
  }
</style>
