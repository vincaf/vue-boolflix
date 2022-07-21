<template>
  <div class="col-2">
    <ul>
        <li><strong>Titolo:</strong> {{ movie.title }}</li>
        <li><strong>Titolo originale:</strong> {{ movie.original_title }}</li>
        <li><strong>Lingua:</strong> {{ movie.original_language }}</li>
        <li><strong>Voto:</strong> {{ movie.vote_average }}</li>
    </ul>
  </div>
</template>

<script>
export default {
    name: 'MovieCard',
    props: {
        'movie': {
            required: true,
            type: Object,
        } 
    },
}
</script>

<style>

</style>