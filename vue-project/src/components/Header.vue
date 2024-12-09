<template>
<header>
    <div class="wrapper">
        <figure>
            <img src="../assets/images/dttlogo.png" alt="dtt logo">
        </figure>
        <nav>
            <a href="/home">Houses</a>
            <a href="/about">About</a>
        </nav>
    </div>
</header>
   
</template>

<script>
export default {
    name:'Header'
}
</script>
<style scoped>
    header{
        width: 100%;
        padding: 2em 2em;
        box-shadow: 0px 0px 11px 0px rgba(199,191,199,1);
        display: none;
        position: sticky;
        top: 0px;
        background-color: var(--light);
        @media screen and (min-width: 980px) {
           display: block;
        }
    }
    
    .wrapper{
        margin: 0 auto;
        display: flex;
        flex-direction: column;
        gap: 4em;
        align-items: center;
        gap: 1em;
        width: 100%;

        @media screen and (min-width: 980px) {
           gap: 5em; 
            width: 1400px;
            flex-direction: row;
        }
    }

    header nav{
        display: flex;
        flex-direction: row;
        gap: 2em;

        @media screen and (min-width: 980px) {
           gap: 5em; 
            width: 1400px;
            flex-direction: row;
        }
    }

    header figure img{
        width: 150px;
    }

    header nav a{
        font-size: 1.2em;
        text-decoration: none;
        color: var(--text-primary);
        transition: ease-out 0.2s;
        &:active, &:hover, &:focus {
        font-weight: 700;
        transition: ease-out 0.2s;
        }
    }


</style>