<script>
    export default {
        name: 'Mobilemenu',
    };
</script>

<template>
    <div class="mobile-menu">
        <nav>
            <a tabindex="" href="#"><svg width="28" height="28" viewBox="0 0 16 16" fill="" xmlns="http://www.w3.org/2000/svg"><path d="M1 6V15H6V11C6 9.89543 6.89543 9 8 9C9.10457 9 10 9.89543 10 11V15H15V6L8 0L1 6Z" /></svg></a>
            <a tabindex="" href="#"><svg width="28" height="28" viewBox="0 0 512 512" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><g id="Page-1" stroke="none" stroke-width="1" fill="" fill-rule="evenodd"><g id="about-white" fill="" transform="translate(42.666667, 42.666667)"><path d="M213.333333,3.55271368e-14 C95.51296,3.55271368e-14 3.55271368e-14,95.51168 3.55271368e-14,213.333333 C3.55271368e-14,331.153707 95.51296,426.666667 213.333333,426.666667 C331.154987,426.666667 426.666667,331.153707 426.666667,213.333333 C426.666667,95.51168 331.154987,3.55271368e-14 213.333333,3.55271368e-14 Z M213.333333,384 C119.227947,384 42.6666667,307.43872 42.6666667,213.333333 C42.6666667,119.227947 119.227947,42.6666667 213.333333,42.6666667 C307.44,42.6666667 384,119.227947 384,213.333333 C384,307.43872 307.44,384 213.333333,384 Z M240.04672,128 C240.04672,143.46752 228.785067,154.666667 213.55008,154.666667 C197.698773,154.666667 186.713387,143.46752 186.713387,127.704107 C186.713387,112.5536 197.99616,101.333333 213.55008,101.333333 C228.785067,101.333333 240.04672,112.5536 240.04672,128 Z M192.04672,192 L234.713387,192 L234.713387,320 L192.04672,320 L192.04672,192 Z" id="Shape"></path></g></g></svg></a>
        </nav>
    </div>
</template>

<style scoped>
    .mobile-menu{
        position: sticky;
        width: 100%;
        bottom: 0;
        box-shadow: 0px 0px 11px 0px rgb(216, 212, 216);
    }
    .mobile-menu nav{
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
        gap: 3em;
        background-color: var(--light);
        padding: 1em 2em;
    }

    .mobile-menu nav a{
        &:active , :focus{
            fill: var(--primary-color);
        }
    }

</style>