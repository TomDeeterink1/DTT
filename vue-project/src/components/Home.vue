<script>

export default {
  props: {
    houses: {
      type: Array,
      default: () => [], 
    },
  },
    name: 'Home', 
}
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
          <input type="text" placeholder="Search for a house"></input>
        </form>
        <form class="buttons">
          <input type="radio" name="filter" value="Price" checked="checked"> 
          <input type="radio" name="filter" value="Size"> 
        </form>
      </section>
      <div class="_houses">
        <ul v-for="house in houses" :key="house.id">
          <li>
            
            <p>{{ house.location.street }}</p>
            <p>Price: {{ house.price }}</p>
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
    
  }

  .full-section ._filters .buttons input:nth-child(1):after{
      position: absolute;
      background-color: var(--tertiar-color-dark);
      content: "Price";
      padding: 1em 5em;
      width: 46%;
      border-radius: 0.4em 0em 0em 0.4em;
      font-weight: 700;
  }

  .full-section ._filters .buttons input:nth-child(1):checked{
    &::after{
      background-color: var(--primary-color);
      color: var(--light);
    }
  }

  .full-section ._filters .buttons input:nth-child(2):after{
      position: absolute;
      background-color: var(--tertiar-color-dark);
      content: "Size";
      padding: 1em 5em;
      border-radius: 0em 0.4em 0.4em 0em;
      width: 46%;
      font-weight: 700;
  }

  .full-section ._filters .buttons input:nth-child(2):checked{
    &::after{
      background-color: var(--primary-color);
      color: var(--light);

    }
  }

</style>