<script>
    import { onMount } from 'svelte';

    let menuToggle;
    let menu;
    let moreDropdown = $state(false);

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
    
    function toggleMoreDropdown() {
        moreDropdown = !moreDropdown;
    }
</script>

<nav class="bg-neutral-100 border-gray-200">
    <div class="max-w-(--breakpoint-xl) flex flex-wrap items-center justify-between mx-auto p-4 pe-0">
        <a href="/" class="flex items-center space-x-3 rtl:space-x-reverse">
            <img src="./arswa_logo.png" class="h-16 w-32" alt="Apex research and Scientific writing academy logo" />
        </a>
        <button data-collapse-toggle="navbar-default" type="button" class="inline-flex items-center p-2 w-10 h-10 justify-center text-sm text-gray-500 rounded-lg lg:hidden hover:bg-gray-100 focus:outline-hidden focus:ring-2 focus:ring-gray-200" aria-controls="navbar-default" aria-expanded="false">
            <span class="sr-only">Open main menu</span>
            <svg class="w-5 h-5" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 17 14">
                <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M1 1h15M1 7h15M1 13h15"/>
            </svg>
        </button>
        <div class="hidden w-full lg:block lg:w-auto p-5 text-xl" id="navbar-default">
            <ul class="font-medium flex flex-col p-4 md:p-0 mt-4 border border-gray-100 rounded-lg bg-neutral-100 lg:flex-row lg:space-x-20 rtl:space-x-reverse lg:mt-0 lg:border-0 ">
                <li class="self-center">
                    <a href="/#work" onclick={toggleMenu} class="block py-2 px-3 text-gray-900 rounded-sm hover:bg-gray-100 lg:hover:bg-transparent lg:border-0 lg:p-0 lg:hover:text-orange-500">Work</a>
                </li>
                <li class="self-center">
                    <a href="/#about" onclick={toggleMenu} class="block py-2 px-3 text-gray-900 rounded-sm hover:bg-gray-100 lg:hover:bg-transparent lg:border-0 lg:p-0 lg:hover:text-orange-500">About</a>
                </li>
                <li class="self-center">
                    <a href="/#contact" onclick={toggleMenu} class="block py-2 px-3 text-gray-900 rounded-sm hover:bg-gray-100 lg:hover:bg-transparent lg:border-0 lg:p-0 lg:hover:text-orange-500">Contact</a>
                </li>
                <li class="self-center relative">
                    <button 
                        onclick={toggleMoreDropdown} 
                        class="flex items-center py-2 px-3 text-gray-900 rounded-sm hover:bg-gray-100 lg:hover:bg-transparent lg:border-0 lg:p-0 lg:hover:text-orange-500"
                    >
                        More
                        <svg class="w-4 h-4 ml-1" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd"></path></svg>
                    </button>
                    {#if moreDropdown}
                        <div class="absolute z-10 mt-2 w-48 bg-white rounded-lg shadow-lg py-1 lg:right-0">
                            <a href="/" onclick={toggleMoreDropdown} class="block px-4 py-2 text-gray-800 hover:bg-gray-100">Groups</a>
                            <a href="/" onclick={toggleMoreDropdown} class="block px-4 py-2 text-gray-800 hover:bg-gray-100">Members</a>
                            <a href="/" onclick={toggleMoreDropdown} class="block px-4 py-2 text-gray-800 hover:bg-gray-100">Blog</a>
                        </div>
                    {/if}
                </li>
                <li class="self-center">
                    <a href="/#" onclick={toggleMenu} class="block py-2 px-3 text-gray-900 rounded-sm hover:bg-gray-100 lg:rounded-full lg:p-3 lg:bg-neutral-100 lg:text-orange-500 lg:border-orange-500 lg:border lg:hover:bg-orange-500 lg:hover:text-neutral-100">Get Started</a>
                </li>
            </ul>
        </div>
    </div>
</nav>
