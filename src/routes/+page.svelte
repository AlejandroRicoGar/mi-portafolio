<script>
    import { onMount } from 'svelte';
    import { FontAwesomeIcon } from '@fortawesome/svelte-fontawesome';
    import { faBars } from '@fortawesome/free-solid-svg-icons';
    import { faCss3, faHtml5, faJsSquare, faNodeJs, faReact, faVuejs, faJava, faGithub } from '@fortawesome/free-brands-svg-icons';
    
    let menuOpen = false;
    function toggleMenu(){
        menuOpen = !menuOpen;
    }

    const skills = [
        {icon: faHtml5, color: "text-orange-600"},
        {icon: faCss3, color: "text-blue-600"},
        {icon: faVuejs, color: "text-green-500"},
        {icon: faNodeJs, color: "text-green-500"},
        {icon: faJava, color: "text-red-500"},
        {icon: faJsSquare, color: "text-yellow-500"},
        {icon: faReact, color: "text-blue-400"},
        {icon: faGithub, color: "text-gray-800"}
    ];

    const Projects = [
        {title: "Password Generator", description: "Password generator ", photo: "/PasswordGenerator.png", link: "https://alejandroricogar.github.io/password-generator.github.io/"},
        {title: "Project 2", description: "Description 2", photo: "https://via.placeholder.com/150", link: "#"},
        {title: "Project 3", description: "Description 3", photo: "https://via.placeholder.com/150", link: "#"},
    ];

    function handleSubmmit(event){
        event.preventDefault();
        const name = document.getElementById("name").value;
        const email = document.getElementById("email").value;
        const message = document.getElementById("message").value;

        alert(`Datos del formulario recibidos: \n Nombre: ${name}\nEmail: ${email} \nMessage: ${message}`)
        
    }
</script>


<header class = "bg-opacity-80 top-0 left-0 z-50 w-full bg-white shadow-lg">
    <nav class="container mx-auto flex items-center justify-between px-6 py-4">
        <div class="text-2xl hover:text-indigo-500">
			<span class="cursor-pointer">&lt;CLB /&gt</span>
		</div>
            <div class="hidden md:flex space-x-4 items-center">
                <a href="about-me" class="text-indigo-500 hover:text-indigo-700 px-3 py-"
                    >About Me</a
                    >
                    <a href="skills" class="text-indigo-500 hover:text-indigo-700 px-3 py-"
                    >Skills</a
                    >
                    <a href="projects" class="text-indigo-500 hover:text-indigo-700 px-3 py-"
                    >Projects</a
                    >
                    <a href="contact" class="text-indigo-500 hover:text-indigo-700 px-3 py-"
                    >Contact</a
                    >
            </div>
        <div class="md:hidden">
            <button on:click={toggleMenu} aria-label="Open menu" class="text-indigo hover:textindigo-700 focus:outline">
                <FontAwesomeIcon icon={faBars} class="text2xl"/>
            </button>
        </div>
    </nav>
    {#if menuOpen}
    <div class="absolute bg-white shadow-md w-full md:hidden">
        <ul class="flex flez-col p-4">
            <li>
                <a href="skills" class="text-indigo-500 hover:text-indigo-700 px-3 py-"
                    >Skills</a
                    >
            </li>
            <li>
                <a href="about me" class="text-indigo-500 hover:text-indigo-700 px-3 py-"
                    >About Me</a
                    >
            </li>
            <li>
                <a href="projects" class="text-indigo-500 hover:text-indigo-700 px-3 py-"
                >Projects</a
                >
            </li>
            <li>
                <a href="contact" class="text-indigo-500 hover:text-indigo-700 px-3 py-"
                    >Contact</a
                    >
            </li>
            
        </ul>
    </div>
    {/if}
</header>

<!--About <Me-->
<section id="about-me" class="py-30 flex flex-col lg:flex-row items-center bg-gradient-br from-teal-400 ">
    <div class = "flex justify-center lg:w-1/3 lg:mb-0">
        <img src="/ejemplo.png" alt="clb dev" class="bg-white rounded-full" />
    </div>
    <div>
        <h1 class="text=5xl font-extrabold leading-tight mb-4">About me</h1>
        <p class="text-lg mt-2 text-gray-300 mb4">Hi my name is Alejandro. I am a web developer</p>
    </div>
</section>

<!--Skills-->
<section id="skills" class="py-30 flex flex-col lg:flex-row items-center bg-gradient-to-br from-teal-400">
    <div class="container mx-auto px-6">
        <h2 class="text-2xl font-bold text-indigo-700 text-center">Skills</h2>
        <div class="grid grid-cols-3 md:grid-cols-4 gap-6 place-items-center">
            {#each skills as skill}
            <div class="group relative p-6 w-1/2 md:w-1/4 lg:w-1/6">
                <FontAwesomeIcon icon={skill.icon} class=""/>
            </div>
            {/each}
        </div>
    </div>
</section>


<!--Projects-->
<section id ="projects" class= "py-30 flex flex-col lg:flex-row items-center bg-gradient-br from-teal-400">
    <h2 class="text=2xl font-bold text-indigo-700 text-center">Projects</h2>
    <div class="mt-6 grid w-full max-w-6xl grid-cols-1 gap-6 px-6 md:grid-cols-2 lg:grid-cols-3"></div>
    {#each Projects as project}
    <div class = "rounded-lg border border-gray-300 bg-white p-4 text-center shadow-md">
        <img src={project.photo} alt={project.title} class="mb-4 h-32 w-full rounded-md object-cover">
        <h3 class = "mb-2 text-xl font-semibold text-indigo-700">{project.title}</h3>
        <p class = "mb-4 text-sm text-gray-700">{project.description}</p>
        <a href={project.link} target = "blank" class="text-indigo-500 hover:text-indigo-700">See Project</a>
    </div>
        
    {/each}
</section>

<!---Contact Form-->
<section id="contact-form" class="py-12 bg-white">
    <div class="container mx-auto px-6 max-w-lg">
        <h2 class="text-2xl font-bold text-indigo-700 text-center">Contact</h2>
        <form class="bg-gray-100 shadow-md rounded px-8 pt-6 pb-8 mb-4" on:submit={handleSubmmit}>
            <div class="mb-4">
                <label class="block text-gray-700 text-sm font-blod mb-2" for="name">Name</label>
                <input class="shadow-md appearance-none border rounded w-full p-2 text-gray-700 focus:outline-none focus:shadow-outline" id="name" type="text" placeholder="Type your name"/>
            </div>
            <div class="mb-4">
                <label class="block text-gray-700 text-sm font-blod mb-2" for="email">Email</label>
                <input class="shadow-md appearance-none border rounded w-full p-2 text-gray-700 focus:outline-none focus:shadow-outline" id="email" type="email" placeholder="Type your email"/>
            </div>
            <div class="mb-4">
                <label class="block text-gray-700 text-sm font-blod mb-2" for="message">Message</label>
                <input class="shadow-md appearance-none border rounded w-full p-2 text-gray-700 focus:outline-none focus:shadow-outline" id="message" type="text" placeholder="Type your message"/>
            </div>
            <div class="flex items-center justify-center">
                <button class="bg-indigo-700 text-white hover:bg-indigo-900 font-bold p-4 rounded focus:outline-none focus:shadow-outline" type="submit">Send </button>
            </div>
        </form>
    </div>
</section>