<script>
export default {
  props: {
    houses: {
      type: Array,
      default: () => [], //retrieve right data
    },
  },
  name: 'Home',
  data() {
    return {
      selectedFilter: 'price', //Ask for price as default
    };
  },
  //Use computed for data reactivity
  computed: {
    //Function to filter the houses
    filteredHouses() {
      //See if the selected filter is equal to price
      if (this.selectedFilter === 'price') {
        //Sort the price with a return ... copy's the array. with a + b the prices are set of to eachother and wil be filter as sutch
        // So when a = bigger then b, it wil go under b. The first item will always be the lower price.
        // - sign is used for comparing the 2.
        return [...this.houses].sort((a, b) => a.price - b.price);
      } else if (this.selectedFilter === 'size') {
        // - Same principle for the size of a house
        return [...this.houses].sort((a, b) => a.size - b.size);
      }
      return this.houses; // Returns the right filterted list
    },
  },
  //methods is used for javascript functions in templates, without this vue wont see it as a function for in the template
  methods: {
    setFilter(filter) {
      this.selectedFilter = filter; // Update the filter type
    },
  },
};
</script>
<template>
  <div class="wrapper">
    <section class="full-section">
      <section class="_topbar">
        <div></div>
        <h1>Houses</h1>
        <button><span>Toevoegen</span><img src="../assets/images/plus-large-svgrepo-com.svg"></button>
      </section>
      <section class="_filters">
        <form>
          <input type="search" placeholder="Search for a house"></input>
          <searc></searc>
        </form>
        <form class="buttons">
            <input type="button" name="filter" value="price" @click="setFilter('price')" checked />
            <input type="button" name="filter" value="size" @click="setFilter('size')" />
        </form>
      </section>
      <div class="_houses">
        <ul>
          <li v-for="house in filteredHouses" :key="house.id">
            <p>{{ house.location.street }}</p>
            <p>Price: {{ house.price }}</p>
            <p>Size: {{ house.size }}</p>
          </li>
        </ul>
      </div>
    </section>
  </div>
</template>


<style scoped>

  .wrapper{
    width: 100%;
    background-color: var( --background-grey);
  }

  .full-section{
    padding: 2em 1em;
    width: 100%;
    display: flex;
    flex-direction: column;
    gap: 2em;
    @media screen and (min-width: 980px) {
          padding: 4em 0em;
          max-width: 1400px;
          margin: 0 auto;
        }
  }
  /* home topbar */
  .full-section ._topbar{
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: 1fr;
    justify-items: center;
    justify-content: end;
    @media screen and (min-width: 980px) {
          display: flex;
          flex-direction: column;
        }
  }

  .full-section ._topbar h1{
    font-size: 1.1em;
    font-weight: 800;
    @media screen and (min-width: 980px) {
      font-size: 2em;
        }
  }

  .full-section ._topbar button{
    border: none;
    background-color: var( --background-grey);
    &:hover{
      cursor: pointer;
    }
  }

  .full-section ._topbar button span{
    display: none;
    @media screen and (min-width: 980px) {
      display: block;
        }
  }

  .full-section ._topbar button img{
    display: inline;
    width: 2em;
  }
  
  /* filters */

  .full-section ._filters{
    width: 100%;
    display: flex;
    flex-direction: column;
    
  }

  .full-section ._filters form input{
    width: 100%;
    padding: 0.5em 1em;
    border-radius: 0.5em;
    border: none;
    font-size: 1em;
    background-color: var(--tertiary-color);
  }

  /* filter buttons */
  .full-section ._filters .buttons{
    padding: 1em 0em;
    display: flex;
    justify-content: space-between;
  }

  .full-section ._filters .buttons input{
    padding: 1em 1em;
    height: 50px;
  }

  .full-section ._filters .buttons input:nth-child(1){
      background-color: var(--tertiar-color-dark);
      width: 46vw;
      height: 50px;
      border-radius: 0.4em 0em 0em 0.4em;
      font-weight: 700;
      &:active , &:focus{
      background-color: var(--primary-color);
      color: var(--light);
      }
  }

    .full-section ._filters .buttons input:nth-child(2){
      background-color: var(--tertiar-color-dark);
      width: 46vw;
      height: 50px;
      border-radius: 0em 0.4em 0.4em 0em;
      font-weight: 700;
      &:active , &:focus{
      background-color: var(--primary-color);
      color: var(--light);
      }
  }




  
</style>