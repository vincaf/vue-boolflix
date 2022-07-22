<template>
  <header>
    <nav class="navbar navbar-dark bg-dark">
      <div class="container-fluid">
        <a class="navbar-brand text-danger fs-3 fw-bold ms-2 ">BOOLFLIX</a>
        <div class="d-flex">
          <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" 
            v-model.trim="searchInput" @keyup.enter="$emit('search', searchInput)">
          <button class="btn btn-outline-danger" type="submit"
            @click.prevent="$emit('search', searchInput)">Search</button>
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  data: function(){
    return{
      searchInput: '',
    }
  }

}
</script>

<style lang="scss" scoped>

</style>