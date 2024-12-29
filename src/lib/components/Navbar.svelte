<script>
    import { onMount } from 'svelte';

    let menuToggle;
    let menu;

    onMount(() => {
        menuToggle = document.querySelector('[data-collapse-toggle="navbar-default"]');
        menu = document.getElementById('navbar-default');

        menuToggle.addEventListener('click', toggleMenu);

        return () => {
            menuToggle.removeEventListener('click', toggleMenu);
        };
    });

    function toggleMenu() {
        const isExpanded = menuToggle.getAttribute('aria-expanded') === 'true';
        menuToggle.setAttribute('aria-expanded', !isExpanded);
        menu.classList.toggle('hidden', isExpanded);
        menu.classList.toggle('flex', !isExpanded);
        menu.classList.toggle('flex-col', !isExpanded);
        menu.classList.toggle('items-center', !isExpanded);
        menu.classList.toggle('justify-center', !isExpanded);
        menu.classList.toggle('space-y-4', !isExpanded);
    }

</script>

<nav class="bg-blue-950 border-gray-200">
    <div class="max-w-screen-xl flex flex-wrap items-center justify-between mx-auto p-4 pe-0">
        <a href="/" class="flex items-center space-x-3 rtl:space-x-reverse">
            <img src="/arswa_logo.png" class="h-16 w-32" alt="Apex research and Scientific writing academy logo" />
        </a>
        <button data-collapse-toggle="navbar-default" type="button" class="inline-flex items-center p-2 w-10 h-10 justify-center text-sm text-gray-500 rounded-lg md:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200" aria-controls="navbar-default" aria-expanded="false">
            <span class="sr-only">Open main menu</span>
            <svg class="w-5 h-5" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 17 14">
                <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 1h15M1 7h15M1 13h15"/>
            </svg>
        </button>
        <div class="hidden w-full md:block md:w-auto p-5" id="navbar-default">
            <ul class="italic flex flex-col p-4 md:p-0 mt-4 border border-gray-100 rounded-lg bg-blue-950 uppercase font-bold md:flex-row md:space-x-8 rtl:space-x-reverse md:mt-0 md:border-0">
                <li class="self-center">
                    <a href="/#" onclick={toggleMenu} class="block py-2 px-3 text-white rounded hover:bg-gray-100 lg:hover:bg-transparent lg:border-0 lg:p-0 lg:hover:text-blue-300 group" aria-current="page"><i class="ph-fill text-white group-hover:text-blue-300 mx-3 ph-house"></i>Home</a>
                </li>
                <li class="self-center">
                    <a href="/#about" onclick={toggleMenu} class="block py-2 px-3 text-white rounded hover:bg-gray-100 lg:hover:bg-transparent lg:border-0 lg:p-0 lg:hover:text-blue-300">About</a>
                </li>
                <li class="self-center">
                    <a href="/#services" onclick={toggleMenu} class="block py-2 px-3 text-white rounded hover:bg-gray-100 lg:hover:bg-transparent lg:border-0 lg:p-0 lg:hover:text-blue-300">Services</a>
                </li>
                <li class="self-center">
                    <a href="/" onclick={toggleMenu} class="block py-2 px-3 text-white rounded hover:bg-gray-100 lg:hover:bg-transparent lg:border-0 lg:p-0 lg:hover:text-blue-300">Contact</a>
                </li>
                
            </ul>
        </div>
    </div>
</nav>
