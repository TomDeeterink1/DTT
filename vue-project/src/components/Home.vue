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
        <button><span>Create new</span><svg width="16" height="16" viewBox="0 0 24 24" fill="" xmlns="http://www.w3.org/2000/svg"><path d="M4 12H20M12 4V20" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/></svg></button>
      </section>
      <section class="_filters">
        <form action="#">
          <input type="search" placeholder="🔍 Search for a house"></input>

        </form>
        <form class="buttons">
            <input type="button" name="filter" value="price" @click="setFilter('price')" checked />
            <input type="button" name="filter" value="size" @click="setFilter('size')" />
        </form>
      </section>
      <div class="_houses">
        <ul>
          <li class="houses_card" v-for="house in filteredHouses" :key="house.id" tabindex="0">
            <a tabindex="1">
              <div class="card_hovermenu">
                <a><svg width="24" height="24" viewBox="-0.5 0 19 19" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:sketch="http://www.bohemiancoding.com/sketch/ns"><g id="out" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd" sketch:type="MSPage"> <path d="M4.91666667,14.8888889 C4.91666667,15.3571429 5.60416667,16 6.0625,16 L12.9375,16 C13.3958333,16 14.0833333,15.3571429 14.0833333,14.8888889 L14.0833333,6 L4.91666667,6 L4.91666667,14.8888889 L4.91666667,14.8888889 L4.91666667,14.8888889 Z M15,3.46500003 L12.5555556,3.46500003 L11.3333333,2 L7.66666667,2 L6.44444444,3.46500003 L4,3.46500003 L4,4.93000007 L15,4.93000007 L15,3.46500003 L15,3.46500003 L15,3.46500003 Z" id="path" fill="#000000" sketch:type="MSShapeGroup"></path></g></svg></a>
                <a><svg width="20" height="20" viewBox="0 0 16 16"  xmlns="http://www.w3.org/2000/svg"><path d="M8.29289 3.70711L1 11V15H5L12.2929 7.70711L8.29289 3.70711Z"/><path d="M9.70711 2.29289L13.7071 6.29289L15.1716 4.82843C15.702 4.29799 16 3.57857 16 2.82843C16 1.26633 14.7337 0 13.1716 0C12.4214 0 11.702 0.297995 11.1716 0.828428L9.70711 2.29289Z"/></svg></a>
              </div>
              <img :src="house.image">
              <!-- image src doesnt need curly bracelets to put trough data -->
              <div>
                <ul class="card_location">
                  <li><p>{{ house.location.street }}</p></li>
                  <li><p>{{ house.price}}</p></li>
                  <li><p>{{ house.location.zip }} {{ house.location.city }}</p></li>
                </ul>
                <ul class="card_details">
                  <li> <svg width="16" height="16" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" clip-rule="evenodd" d="M10.9436 3.25H13.0564C14.8942 3.24998 16.3498 3.24997 17.489 3.40314C18.6614 3.56076 19.6104 3.89288 20.3588 4.64124C21.1071 5.38961 21.4392 6.33856 21.5969 7.51098C21.7482 8.63675 21.75 10.0715 21.75 11.8787C22.0939 12.1624 22.3669 12.5282 22.5407 12.9476C22.661 13.238 22.7076 13.5375 22.7292 13.8546C22.75 14.1592 22.75 14.5303 22.75 14.9747V15.0253C22.75 15.4697 22.75 15.8408 22.7292 16.1454C22.7076 16.4625 22.661 16.762 22.5407 17.0524C22.2616 17.7262 21.7262 18.2616 21.0524 18.5407C20.762 18.661 20.4625 18.7076 20.1454 18.7292C20.0242 18.7375 19.8926 18.7425 19.75 18.7455V20C19.75 20.4142 19.4142 20.75 19 20.75C18.5858 20.75 18.25 20.4142 18.25 20V18.75H5.75V20C5.75 20.4142 5.41421 20.75 5 20.75C4.58579 20.75 4.25 20.4142 4.25 20V18.7455C4.10741 18.7425 3.97577 18.7375 3.85464 18.7292C3.53754 18.7076 3.23801 18.661 2.94762 18.5407C2.27379 18.2616 1.73844 17.7262 1.45933 17.0524C1.33905 16.762 1.29241 16.4625 1.27077 16.1454C1.24999 15.8408 1.24999 15.4697 1.25 15.0253V14.9748C1.24999 14.5303 1.24999 14.1592 1.27077 13.8546C1.29241 13.5375 1.33905 13.238 1.45933 12.9476C1.63307 12.5282 1.90609 12.1624 2.25 11.8787C2.25001 10.0715 2.25178 8.63675 2.40314 7.51098C2.56076 6.33856 2.89288 5.38961 3.64124 4.64124C4.38961 3.89288 5.33856 3.56076 6.51098 3.40314C7.65019 3.24997 9.10582 3.24998 10.9436 3.25ZM3.75039 11.2789C3.78493 11.2758 3.81968 11.2732 3.85464 11.2708C4.1064 11.2536 4.40354 11.2506 4.75 11.2501L4.75 10.448C4.74997 9.54952 4.74995 8.8003 4.82991 8.20552C4.91432 7.57773 5.09999 7.01093 5.55546 6.55546C6.01093 6.09999 6.57773 5.91432 7.20552 5.82991C7.8003 5.74995 8.54952 5.74997 9.448 5.75H14.552C15.4505 5.74997 16.1997 5.74995 16.7945 5.82991C17.4223 5.91432 17.9891 6.09999 18.4445 6.55546C18.9 7.01093 19.0857 7.57773 19.1701 8.20552C19.2501 8.8003 19.25 9.54952 19.25 10.448V11.2501C19.5965 11.2506 19.8936 11.2536 20.1454 11.2708C20.1803 11.2732 20.2151 11.2758 20.2496 11.2789C20.2472 9.74405 20.2303 8.60396 20.1102 7.71085C19.975 6.70476 19.7213 6.12511 19.2981 5.7019C18.8749 5.27869 18.2952 5.02502 17.2892 4.88976C16.2615 4.75159 14.9068 4.75 13 4.75H11C9.09318 4.75 7.73851 4.75159 6.71085 4.88976C5.70476 5.02502 5.12511 5.27869 4.7019 5.7019C4.27869 6.12511 4.02502 6.70476 3.88976 7.71085C3.76968 8.60396 3.75276 9.74405 3.75039 11.2789ZM17.75 11.25V10.5C17.75 9.53599 17.7484 8.88843 17.6835 8.40539C17.6214 7.94393 17.5142 7.74643 17.3839 7.61612C17.2536 7.4858 17.0561 7.37858 16.5946 7.31654C16.1116 7.25159 15.464 7.25 14.5 7.25H12.75V11.25H17.75ZM11.25 11.25V7.25H9.5C8.53599 7.25 7.88843 7.25159 7.40539 7.31654C6.94393 7.37858 6.74643 7.4858 6.61612 7.61612C6.4858 7.74643 6.37858 7.94393 6.31654 8.40539C6.25159 8.88843 6.25 9.53599 6.25 10.5V11.25H11.25ZM3.95674 12.7673C3.71602 12.7837 3.5988 12.8132 3.52165 12.8452C3.21536 12.972 2.97202 13.2154 2.84515 13.5216C2.81319 13.5988 2.78372 13.716 2.76729 13.9567C2.75041 14.2042 2.75 14.5238 2.75 15C2.75 15.4762 2.75041 15.7958 2.76729 16.0433C2.78372 16.284 2.81319 16.4012 2.84515 16.4784C2.97202 16.7846 3.21536 17.028 3.52165 17.1549C3.5988 17.1868 3.71602 17.2163 3.95674 17.2327C4.20421 17.2496 4.5238 17.25 5 17.25H19C19.4762 17.25 19.7958 17.2496 20.0433 17.2327C20.284 17.2163 20.4012 17.1868 20.4784 17.1549C20.7846 17.028 21.028 16.7846 21.1549 16.4784C21.1868 16.4012 21.2163 16.284 21.2327 16.0433C21.2496 15.7958 21.25 15.4762 21.25 15C21.25 14.5238 21.2496 14.2042 21.2327 13.9567C21.2163 13.716 21.1868 13.5988 21.1549 13.5216C21.028 13.2154 20.7846 12.972 20.4784 12.8452C20.4012 12.8132 20.284 12.7837 20.0433 12.7673C19.7958 12.7504 19.4762 12.75 19 12.75H5C4.5238 12.75 4.20421 12.7504 3.95674 12.7673Z" fill="#1C274C"/></svg> {{ house.rooms.bedrooms }} </li>
                  <li> <svg fill="#000000" width="16" height="16" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M22,12H5V5A2,2,0,0,1,7,3H9a2,2,0,0,1,1.838,1.214A3.5,3.5,0,0,0,8.5,7.5V9a1,1,0,0,0,1,1h5a1,1,0,0,0,1-1V7.5a3.5,3.5,0,0,0-2.6-3.368A4,4,0,0,0,9,1H7A4,4,0,0,0,3,5v7H2a1,1,0,0,0,0,2H3v4a3,3,0,0,0,2,2.816V22a1,1,0,0,0,2,0V21H17v1a1,1,0,0,0,2,0V20.816A3,3,0,0,0,21,18V14h1a1,1,0,0,0,0-2ZM13.5,7.5V8h-3V7.5a1.5,1.5,0,0,1,3,0ZM19,18a1,1,0,0,1-1,1H6a1,1,0,0,1-1-1V14H19Z"/></svg> {{ house.rooms.bathrooms }}  </li>
                  <li> <svg fill="#000000" height="16" width="16" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 100 100" xml:space="preserve"><g id="turf-size"><path d="M76.647,30.353c-1.104,0-2-0.896-2-2v-3h-3c-1.104,0-2-0.896-2-2s0.896-2,2-2h5c1.104,0,2,0.896,2,2v5C78.647,29.457,77.752,30.353,76.647,30.353z"/><path d="M62.988,25.353h-8.659c-1.104,0-2-0.896-2-2s0.896-2,2-2h8.659c1.104,0,2,0.896,2,2S64.093,25.353,62.988,25.353z"/><path d="M45.67,25.353h-8.659c-1.104,0-2-0.896-2-2s0.896-2,2-2h8.659c1.104,0,2,0.896,2,2S46.775,25.353,45.67,25.353z"/><path d="M23.353,30.353c-1.104,0-2-0.896-2-2v-5c0-1.104,0.896-2,2-2h5c1.104,0,2,0.896,2,2s-0.896,2-2,2h-3v3C25.353,29.457,24.457,30.353,23.353,30.353z"/><path d="M23.353,64.988c-1.104,0-2-0.896-2-2v-8.659c0-1.104,0.896-2,2-2s2,0.896,2,2v8.659C25.353,64.093,24.457,64.988,23.353,64.988z"/><path d="M23.353,47.67c-1.104,0-2-0.896-2-2v-8.659c0-1.104,0.896-2,2-2s2,0.896,2,2v8.659C25.353,46.775,24.457,47.67,23.353,47.67z"/><path d="M28.353,78.647h-5c-1.104,0-2-0.896-2-2v-5c0-1.104,0.896-2,2-2s2,0.896,2,2v3h3c1.104,0,2,0.896,2,2S29.457,78.647,28.353,78.647z"/><path d="M62.988,78.647h-8.659c-1.104,0-2-0.896-2-2s0.896-2,2-2h8.659c1.104,0,2,0.896,2,2S64.093,78.647,62.988,78.647z"/><path d="M45.67,78.647h-8.659c-1.104,0-2-0.896-2-2s0.896-2,2-2h8.659c1.104,0,2,0.896,2,2S46.775,78.647,45.67,78.647z"/><path d="M76.647,78.647h-5c-1.104,0-2-0.896-2-2s0.896-2,2-2h3v-3c0-1.104,0.896-2,2-2s2,0.896,2,2v5C78.647,77.752,77.752,78.647,76.647,78.647z"/><path d="M76.647,64.988c-1.104,0-2-0.896-2-2v-8.659c0-1.104,0.896-2,2-2s2,0.896,2,2v8.659C78.647,64.093,77.752,64.988,76.647,64.988z"/><path d="M76.647,47.67c-1.104,0-2-0.896-2-2v-8.659c0-1.104,0.896-2,2-2s2,0.896,2,2v8.659C78.647,46.775,77.752,47.67,76.647,47.67z"/><path d="M90.216,92.216H9.784c-1.104,0-2-0.896-2-2V9.784c0-1.104,0.896-2,2-2h80.432c1.104,0,2,0.896,2,2v80.432C92.216,91.32,91.32,92.216,90.216,92.216z M11.784,88.216h76.432V11.784H11.784V88.216z"/></g><g id="Layer_1"></g></svg> {{ house.size }}  </li>
              </ul>
              </div>
            </a>
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
    gap: 1em;
    @media screen and (min-width: 980px) {
          padding: 4em 1em;
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
        flex-direction: row;
        padding: 1em 0em;
        justify-content: space-between;
        align-items: center;
        width: 100%;
        & div:nth-child(1){
          display: none;
        }
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
    display: flex;
    align-items: center;
    flex-direction: row;
    
    @media screen and (min-width: 980px) {
      display: flex;
      align-items: center;
      flex-direction: row-reverse;
      gap: 1em;
      padding: 1em 2em;
      background-color: var(--primary-color);
      border-radius: 6px;
      transition: 0.3s ease-out;
      color: var(--light);
        &:hover{
          transition: 0.3s ease-out;
          transform: scale(94%);
          cursor: pointer;
    
        }
      }
  }

  .full-section ._topbar button span{
    display: none;
    @media screen and (min-width: 980px) {
      display: block;
      font-weight: 600;
      text-transform: uppercase;
      }
  }

  .full-section ._topbar button > svg{
    display: inline;
    width: 2em;
    height: 2em;
    position: absolute;
    border-radius: 2px;
    right: 2em;
    background-color: var(--primary-color);
    @media screen and (min-width: 980px) {
      position: inherit;
      margin-top: 0px;
      right: 0em;
      width: 1.2em;
      fill: var(--light);
      background-color: inherit;
    }
  }
  
  /* filters */

  .full-section ._filters{
    width: 100%;
    display: flex;
    flex-direction: column;
    @media screen and (min-width: 980px) {
      flex-direction: row;
      align-items: center;
      justify-content: space-between;
    }
    
  }

  .full-section ._filters form input{
    width: 100%;
    padding: 0.5em 1em;
    border-radius: 0.5em;
    border: none;
    font-size: 1em;
    background-color: var(--tertiary-color);

  }

  .full-section ._filters form:nth-child(1){
    @media screen and (min-width: 980px) {
      min-width: 400px;
    }
  }

  /* filter buttons */
  .full-section ._filters .buttons{
    padding: 1em 0em;
    display: flex;
    justify-content: space-between;
  }

  .full-section ._filters .buttons input{
    height: 40px;
    }

  .full-section ._filters .buttons input:nth-child(1){
      background-color: var(--tertiar-color-dark);
      width: 46vw;
      border-radius: 0.4em 0em 0em 0.4em;
      font-weight: 700;
      &:active , &:focus{
      background-color: var(--primary-color);
      color: var(--light);
      }
      @media screen and (min-width: 410px) and (max-width: 980px) {
        width: 50vw;
      }
      @media screen and (min-width: 980px) {
      width: inherit;
      padding: 0em 4em;
      }
  }

    .full-section ._filters .buttons input:nth-child(2){
      background-color: var(--tertiar-color-dark);
      width: 46vw;
      border-radius: 0em 0.4em 0.4em 0em;
      font-weight: 700;
      &:active , &:focus{
      background-color: var(--primary-color);
      color: var(--light);
      }
      @media screen and (min-width: 410px) and (max-width: 980px) {
        width: 50vw;
      }
      @media screen and (min-width: 980px) {
        width: inherit;
      padding: 0em 4em;
      }
  }

  /* Houses list */
  ._houses{
    margin-top: -1em;
  }

  ._houses ul{
    padding-inline-start: 0px;
    display: flex;
    flex-direction: column;
    gap: 1em;
  }

  /* Houses cards */

 .houses_card{
  list-style: none;
  padding: 1em;
  border-radius: 1em;
  background-color: var(--light);
  box-shadow: 0px 0px 6px 0px rgb(233, 232, 233);
 }

 .houses_card a{
  display: flex;
  gap: 0.75em;
  flex-direction: row;
  width: 100%;
  
  & img{
    transition: ease-out 0.3s;
  }

  &:focus > img{
    transition: ease-out 0.3s;
    transform: scale(105%);
    cursor: pointer;
  }

  &:focus > .card_hovermenu{
    display: block;
    position: absolute;
    display: flex;
    flex-direction: row;
    align-items: center;
    gap: 0.3em;
    right: 2em;
    & button{
      border: none;
      padding: none;
      background-color: var(--light);
    }

    & svg{
      &:focus,:active,:hover{
        fill: var(--primary-color);
        cursor: pointer;
      }
    }

  }
  @media screen and (min-width: 980px) {
       &:hover {
          cursor: pointer;
          img{
            transition: ease-out 0.3s;
          transform: scale(105%);
          cursor: pointer;
          border-radius: 4px;

        }
      }
 }

 }
 .houses_card .card_hovermenu{
  display: none;
 }

  .houses_card img{
  width: 100px;
  height: 100px;
  background-color: var(--dark);
 }

  .houses_card div{
  display: flex;
  flex-direction: column;
  gap: 1em;
 }

  .houses_card div .card_location{
  gap: 0em;
  display: flex;
  flex-direction: column;
  }

 .houses_card div .card_location li{
  padding-inline-start: 0px;
  list-style: none;
 }

 .houses_card div .card_location li:nth-child(1) p:nth-child(1){
  font-weight: 800;
 }

 .houses_card  div .card_details{
  padding-inline-start: 0px;
  list-style: none;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: 1fr;
  grid-column-gap: 0.5em;
  grid-row-gap: 0px;
 }

</style>