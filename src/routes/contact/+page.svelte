<script>
    // Import any necessary Svelte functionality
    import { onMount } from 'svelte';
    
    // Form data
    let firstName = '';
    let lastName = '';
    let email = '';
    let message = '';
    
    // Form submission handler
    const handleSubmit = (event) => {
        event.preventDefault();
        // Handle form submission logic here
        console.log({ firstName, lastName, email, message });
        // Reset form after submission
        firstName = '';
        lastName = '';
        email = '';
        message = '';
        alert('Message sent successfully!');
    };
    
    onMount(() => {
        // Load phosphor icons if needed
        // This assumes phosphor icons are already included in your project
    });
</script>

<svelte:head>
    <title>Contact Us | Apex Scientific Editing</title>
    <link rel="stylesheet" href="https://unpkg.com/phosphor-icons/src/css/icons.css">
</svelte:head>

<section class="w-full p-5 bg-stone-500" id="contact">
    <div class="max-w-screen-2xl mx-auto">
        <h2 class="text-5xl font-semibold text-center mb-10 text-neutral-200">Contact Us</h2>
        
        <div class="flex flex-col md:flex-row bg-white">
            <div class="md:w-1/3 p-8">
                <p class="mb-5">
                    Get in touch with Academy Writing Community for any
                    inquiries or collaborations. We'd love to hear from you!
                </p>
                
                <div class="mb-5">
                    <p class="font-medium mb-2">Contact Information</p>
                    
                    <div class="flex items-start mb-3">
                        <i class="ph ph-phone text-xl mr-3 mt-1"></i>
                        <p>Phone: (+1) 919-943-2704</p>
                    </div>
                    
                    <div class="flex items-start mb-3">
                        <i class="ph ph-envelope text-xl mr-3 mt-1"></i>
                        <p>Email: arswacademy@gmail.com</p>
                    </div>
                    
                    <div class="flex items-start mb-3">
                        <i class="ph ph-map-pin text-xl mr-3 mt-1"></i>
                        <p>Location: Cary NC</p>
                    </div>
                </div>
                
                <div class="flex gap-2 mt-5">
                    <a href="https://facebook.com" target="_blank" rel="noopener noreferrer" aria-label="Visit our Facebook page" class="bg-black text-white rounded-full p-2 w-8 h-8 flex items-center justify-center">
                        <i class="ph ph-facebook-logo"></i>
                    </a>
                    <a href="https://twitter.com" target="_blank" rel="noopener noreferrer" aria-label="Visit our Twitter page" class="bg-black text-white rounded-full p-2 w-8 h-8 flex items-center justify-center">
                        <i class="ph ph-twitter-logo"></i>
                    </a>
                    <a href="https://linkedin.com" target="_blank" rel="noopener noreferrer" aria-label="Visit our LinkedIn page" class="bg-black text-white rounded-full p-2 w-8 h-8 flex items-center justify-center">
                        <i class="ph ph-linkedin-logo"></i>
                    </a>
                    <a href="https://instagram.com" target="_blank" rel="noopener noreferrer" aria-label="Visit our Instagram page" class="bg-black text-white rounded-full p-2 w-8 h-8 flex items-center justify-center">
                        <i class="ph ph-instagram-logo"></i>
                    </a>
                </div>
            </div>
            <div class="md:w-2/3 p-8">
                <form onsubmit={(event) => handleSubmit(event)}>
                    <div class="mb-5">
                        <label for="firstName" class="block mb-2">First Name</label>
                        <input 
                            id="firstName"
                            type="text" 
                            class="w-full border border-gray-300 p-2 mb-4"
                            bind:value={firstName}
                        />
                    </div>
                    
                    <div class="mb-5">
                        <label for="lastName" class="block mb-2">Last Name</label>
                        <input 
                            id="lastName"
                            type="text" 
                            class="w-full border border-gray-300 p-2 mb-4"
                            bind:value={lastName}
                        />
                    </div>
                    
                    <div class="mb-5">
                        <label for="email" class="block mb-2">Email *</label>
                        <input 
                            id="email"
                            type="email" 
                            class="w-full border border-gray-300 p-2 mb-4" 
                            required
                            bind:value={email}
                        />
                    </div>
                    
                    <div class="mb-5">
                        <label for="message" class="block mb-2">Message</label>
                        <textarea 
                            id="message"
                            class="w-full border border-gray-300 p-2 h-32 mb-4"
                            bind:value={message}
                        ></textarea>
                    </div>
                    
                    <button 
                        type="submit"
                        class="bg-black text-white py-2 px-4 w-full hover:bg-gray-800 transition-colors"
                    >
                        Send Message
                    </button>
                </form>
            </div>
        </div>
    </div>
</section>