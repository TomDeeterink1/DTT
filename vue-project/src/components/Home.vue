<template>
  <div class="wrapper">
    <section>
      <section class="topbar">
        <h1>Houses</h1>
        <button>Create New</button>
      </section>
      <section class="filters">
        <form>
          <input type="text" placeholder="Wat zoekt u"></input>
        </form>
        <div>
          <button></button>
          <button></button>
        </div>
      </section>
      <div class="houses">
        <li v-for="house in houses">
        {{ house.price }}
      </li>
      </div>
    </section>
  </div>
</template>

<script>

export default {
    name: 'Home',
}
</script>

<style>

</style>