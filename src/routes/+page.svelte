<script lang="ts">
  import { shuffle } from 'lodash-es';

  // Define types for the data structures
  type Name = {
    firstName: string;
    lastName: string;
    movies: number;
    age: number;
  };

  let names: Name[] = [
    { firstName: 'Tony', lastName: 'Stark', movies: 10, age: 45 },
    { firstName: 'Steve', lastName: 'Rogers', movies: 9, age: 100 },
    { firstName: 'Thor', lastName: 'Odinson', movies: 8, age: 1500 },
    { firstName: 'Bruce', lastName: 'Banner', movies: 6, age: 50 },
    { firstName: 'Natasha', lastName: 'Romanoff', movies: 7, age: 36 },
    { firstName: 'Clint', lastName: 'Barton', movies: 6, age: 45 },
    { firstName: 'Peter', lastName: 'Parker', movies: 5, age: 22 },
    { firstName: 'Wanda', lastName: 'Maximoff', movies: 5, age: 30 },
    { firstName: 'Stephen', lastName: 'Strange', movies: 4, age: 42 },
    { firstName: 'Scott', lastName: 'Lang', movies: 3, age: 45 }
  ];

  let casts: string[] = ['Tony', 'captain', 'thor'];

  function handleShuffle(): void {
    names = shuffle([...names]); // Create a new array and shuffle it
  }

  function handleShuffle1(): void {
    casts = shuffle([...casts]); // Create a new array and shuffle it
  }
</script>

<main>
  <button on:click={handleShuffle} class="shuffle-button">Shuffle Names</button>
  <table>
    <thead>
      <tr>
        <th>#</th>
        <th>First Name</th>
        <th>Last Name</th>
        <th>Movies</th>
        <th>Age</th>
        <th>Placeholder</th>
      </tr>
    </thead>
    <tbody>
      {#each names as { firstName, lastName, movies, age }, index (firstName)}
        <tr>
          <td>{index + 1}</td>
          <td>{firstName}</td>
          <td>{lastName}</td>
          <td>{movies}</td>
          <td>{age}</td>
          <td><input placeholder="Table placeholder" /></td>
        </tr>
      {/each}
    </tbody>
  </table>
  <button on:click={handleShuffle1} class="shuffle-button">Shuffle Casts</button>
  {#each casts as name (name)}
    <h2>{name}</h2>
    <input placeholder="Cast placeholder" />
  {/each}
</main>

<style>
  /* Styling for the main container, centers the content and restricts the width */
  main {
    text-align: center;
    padding: 1em;
    max-width: 800px;
    margin: 0 auto;
  }

  table {
    width: 100%;
    border-collapse: collapse;
    margin: 1em 0;
  }

  th, td {
    border: 1px solid #ddd;
    padding: 0.8em;
    text-align: left;
  }

  th {
    background-color: #f4f4f4;
  }

  .shuffle-button {
    padding: 0.5em 1em;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 1em;
    margin-bottom: 1em;
  }

  .shuffle-button:hover {
    background-color: #0056b3;
  }
</style>
