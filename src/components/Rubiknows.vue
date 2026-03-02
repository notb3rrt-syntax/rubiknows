<script>
export default {
    data() {
        return {
            isOpen: false,
            animateHeroLabel: false,
            animateHeroHeading: false,
            animateHeroParagraph: false,
            animateHeroButtons: false,
            animateAbout: false,
            animateServices: false,
            animateProjects: false,
            animateContact: false,
            img: '../logo.png',
            maam: '../maam.png',
            showMore: false,
            showMore: false,
            projects: [
                {
                    title: "Commercial Building",
                    description: "A modern office complex built with precision and high-quality materials.",
                    image: "https://i.pinimg.com/736x/cd/43/59/cd4359eb5b895ce4cda433d55de3d608.jpg",
                    iconPath: "M3 21h18M5 21V7l7-4 7 4v14" // minimalist building icon
                },
                {
                    title: "Residential Complex",
                    description: "Sustainable residential project designed for comfort and safety.",
                    image: "https://i.pinimg.com/1200x/2b/a9/95/2ba995140fe081b838357573ca1232b4.jpg",
                    iconPath: "M12 2l4 8H8l4-8z" // roof icon
                },
                {
                    title: "Industrial Facility",
                    description: "Large-scale industrial building built with robust engineering standards.",
                    image: "https://i.pinimg.com/1200x/30/0b/95/300b9516d1f7344d100fe03aba3d2859.jpg",
                    iconPath: "M5 13l4 4L19 7" // check mark icon
                },
                {
                    title: "Bridge Construction",
                    description: "Engineering precision for large-scale infrastructure projects.",
                    image: "https://i.pinimg.com/736x/3d/c9/c3/3dc9c31e1703ac5a10a04f740203f6ec.jpg",
                    iconPath: "M13 3v10h8"
                },
                {
                    title: "Skyscraper",
                    description: "Modern high-rise buildings with innovative design solutions.",
                    image: "https://i.pinimg.com/1200x/1d/1c/08/1d1c0847c6988acf6b965535398c4f00.jpg",
                    iconPath: "M3 3h18v18H3z"
                },
                {
                    title: "Warehouse Facility",
                    description: "Efficient industrial spaces built with safety and durability in mind.",
                    image: "https://i.pinimg.com/1200x/44/f3/27/44f327b88768402be361969f9e50c603.jpg",
                    iconPath: "M12 4v16"
                }
            ],
            modalProject: null,
            projects: [
                {
                    image: 'https://i.pinimg.com/736x/cd/43/59/cd4359eb5b895ce4cda433d55de3d608.jpg',
                    title: 'Commercial Building',
                    description: 'A modern office complex built with precision and high-quality materials.',
                    iconPath: 'M3 3h18v18H3V3z'
                },
                {
                    image: 'https://i.pinimg.com/1200x/2b/a9/95/2ba995140fe081b838357573ca1232b4.jpg',
                    title: 'Residential Complex',
                    description: 'A sustainable residential project designed for comfort and safety.',
                    iconPath: 'M12 2l9 7v13H3V9l9-7z'
                },
                {
                    image: 'https://i.pinimg.com/1200x/30/0b/95/300b9516d1f7344d100fe03aba3d2859.jpg',
                    title: 'Industrial Facility',
                    description: 'A large-scale industrial building built with robust engineering standards.',
                    iconPath: 'M4 4h16v16H4V4z'
                },
                {
                    image: 'https://i.pinimg.com/736x/3d/c9/c3/3dc9c31e1703ac5a10a04f740203f6ec.jpg',
                    title: 'Bridge Construction',
                    description: 'Engineering precision for large-scale infrastructure projects.',
                    iconPath: 'M2 12h20M12 2v20'
                },
                {
                    image: 'https://i.pinimg.com/1200x/1d/1c/08/1d1c0847c6988acf6b965535398c4f00.jpg',
                    title: 'Skyscraper',
                    description: 'Modern high-rise buildings with innovative design solutions.',
                    iconPath: 'M6 22V2h12v20H6z'
                },
                {
                    image: 'https://i.pinimg.com/1200x/44/f3/27/44f327b88768402be361969f9e50c603.jpg',
                    title: 'Warehouse Facility',
                    description: 'Efficient industrial spaces built with safety and durability in mind.',
                    iconPath: 'M3 6h18v12H3V6z'
                },
            ]
        };
    },


    mounted() {
        const observer = new IntersectionObserver(
            (entries) => {
                entries.forEach((entry) => {
                    if (entry.isIntersecting) {
                        switch (entry.target.id) {
                            case "hero-label":
                                this.animateHeroLabel = true;
                                break;
                            case "hero-heading":
                                this.animateHeroHeading = true;
                                break;
                            case "hero-paragraph":
                                this.animateHeroParagraph = true;
                                break;
                            case "hero-buttons":
                                this.animateHeroButtons = true;
                                break;
                            case "about-section":
                                this.animateAbout = true;
                                break;
                            case "services-section":
                                this.animateServices = true;
                                break;
                            case "projects-section":
                                this.animateProjects = true;
                                break;
                            case "contact-section":
                                this.animateContact = true;
                                break;
                        }
                    }
                });
            },
            { threshold: 0.2 }
        );

        observer.observe(this.$refs.heroLabel);
        observer.observe(this.$refs.heroHeading);
        observer.observe(this.$refs.heroParagraph);
        observer.observe(this.$refs.heroButtons);
        observer.observe(this.$refs.aboutSection);
        observer.observe(this.$refs.servicesSection);
        observer.observe(this.$refs.projectsSection);
        observer.observe(this.$refs.contactSection);
    },

    methods: {
        toggleProjects() {
            this.showMore = !this.showMore;
        },
        toggleProjects() {
            this.showMore = !this.showMore;
        },
        openModal(project) {
            this.modalProject = project;
            this.modalIndex = this.projects.indexOf(project); // store index
            document.body.style.overflow = 'hidden';
        },
        closeModal() {
            this.modalProject = null;
            this.modalIndex = null;
            document.body.style.overflow = '';
        },
        prevProject() {
            if (this.modalIndex > 0) {
                this.modalIndex--;
            } else {
                this.modalIndex = this.projects.length - 1; // loop to last
            }
            this.modalProject = this.projects[this.modalIndex];
        },
        nextProject() {
            if (this.modalIndex < this.projects.length - 1) {
                this.modalIndex++;
            } else {
                this.modalIndex = 0; // loop to first
            }
            this.modalProject = this.projects[this.modalIndex];
        }
    }

}

</script>

<style>
/* Optional: smooth scroll for anchor links */
html {
    scroll-behavior: smooth;
}

@keyframes spin-slow {
    from {
        transform: rotate(0deg);
    }

    to {
        transform: rotate(360deg);
    }
}

.animate-spin-slow {
    animation: spin-slow 40s linear infinite;
}

@keyframes spin-slow {
    0% {
        transform: rotate(0deg);
    }

    50% {
        transform: rotate(1deg);
    }

    100% {
        transform: rotate(0deg);
    }
}

.animate-spin-slow {
    animation: spin-slow 8s infinite ease-in-out;
}

@keyframes pulse-slow {

    0%,
    100% {
        transform: scale(1);
        opacity: 0.3;
    }

    50% {
        transform: scale(1.1);
        opacity: 0.5;
    }
}

.animate-pulse-slow {
    animation: pulse-slow 6s infinite ease-in-out;
}
</style>

<template>
    <!-- ================= NAVBAR ================= -->
    <header class="fixed w-full top-0 z-50 backdrop-blur-md bg-gray-950/50 border-b border-gray-700 shadow-lg">
        <nav class="max-w-7xl mx-auto px-6 py-4 flex justify-between items-center">

            <!-- Logo / Brand -->
            <div class="cursor-pointer text-white font-bold text-xl tracking-widest uppercase">
                Rubi<span class="text-orange-600 text-2xl">knows</span>
            </div>

            <!-- Desktop Menu -->
            <ul class="hidden md:flex items-center space-x-10 text-gray-300 font-medium">
                <li>
                    <a href="#hero" class="relative group hover:text-orange-400 transition duration-300">
                        Home
                        <span
                            class="absolute left-0 -bottom-1 w-0 h-0.5 bg-orange-400 transition-all duration-300 group-hover:w-full"></span>
                    </a>
                </li>

                <li>
                    <a href="#about" class="relative group hover:text-orange-400 transition duration-300">
                        About
                        <span
                            class="absolute left-0 -bottom-1 w-0 h-0.5 bg-orange-400 transition-all duration-300 group-hover:w-full"></span>
                    </a>
                </li>

                <li>
                    <a href="#services" class="relative group hover:text-orange-400 transition duration-300">
                        Services
                        <span
                            class="absolute left-0 -bottom-1 w-0 h-0.5 bg-orange-400 transition-all duration-300 group-hover:w-full"></span>
                    </a>
                </li>

                <li>
                    <a href="#projects" class="relative group hover:text-orange-400 transition duration-300">
                        Projects
                        <span
                            class="absolute left-0 -bottom-1 w-0 h-0.5 bg-orange-400 transition-all duration-300 group-hover:w-full"></span>
                    </a>
                </li>

                <li>
                    <a href="#contact" class="relative group hover:text-orange-400 transition duration-300">
                        Contact
                        <span
                            class="absolute left-0 -bottom-1 w-0 h-0.5 bg-orange-400 transition-all duration-300 group-hover:w-full"></span>
                    </a>
                </li>
            </ul>

            <!-- Professional White CTA -->
            <div class="hidden md:block">
                <button
                    class="bg-white text-gray-900 font-semibold px-7 py-2.5 rounded-md border border-gray-300 hover:bg-gray-100 transition duration-300 shadow-md hover:shadow-lg">
                    Get a Free Quote
                </button>
            </div>

            <!-- Mobile Button -->
            <button class="md:hidden flex flex-col space-y-1.5" @click="isOpen = !isOpen">
                <span
                    :class="['w-6 h-0.5 bg-white transition duration-300', isOpen ? 'rotate-45 translate-y-2' : '']"></span>
                <span :class="['w-6 h-0.5 bg-white transition duration-300', isOpen ? 'opacity-0' : '']"></span>
                <span
                    :class="['w-6 h-0.5 bg-white transition duration-300', isOpen ? '-rotate-45 -translate-y-2' : '']"></span>
            </button>
        </nav>

        <!-- Mobile Menu -->
        <div v-if="isOpen" class="md:hidden bg-gray-950 border-t border-gray-700 px-6 py-6 space-y-6 text-gray-300">
            <a href="#hero" class="block hover:text-orange-400 transition">Home</a>
            <a href="#about" class="block hover:text-orange-400 transition">About</a>
            <a href="#services" class="block hover:text-orange-400 transition">Services</a>
            <a href="#projects" class="block hover:text-orange-400 transition">Projects</a>
            <a href="#contact" class="block hover:text-orange-400 transition">Contact</a>

            <button
                class="w-full bg-white text-gray-900 font-semibold px-5 py-3 rounded-md border border-gray-300 hover:bg-gray-100 transition duration-300 shadow-md">
                Start Your Project
            </button>
        </div>
    </header>

    <div class="h-20"></div>

    <!-- ================= HERO ================= -->
    <section id="hero" class="relative bg-black text-white overflow-hidden">
        <!-- Background -->
        <div class="absolute inset-0 bg-cover bg-center opacity-30"
            style="background-image: url('https://i.pinimg.com/736x/47/75/93/477593fdb78a813aafccb3d1cedaa0df.jpg');">
        </div>
        <div class="absolute inset-0 bg-gradient-to-r from-black via-black/70 to-black/90"></div>

        <img :src="img" alt=""
            class="absolute top-0 left-1/2 transform -translate-x-1/2 w-32 sm:w-40 md:w-48 lg:w-56 opacity-80 pointer-events-none" />
        <div class="relative max-w-7xl mx-auto px-6 py-28 md:py-40 text-center mt-10">
            <p ref="heroLabel" id="hero-label"
                :class="animateHeroLabel ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-6'"
                class="text-orange-500 uppercase tracking-widest text-sm mb-4 transition-all duration-700">
                Trusted Engineering & Construction Experts
            </p>

            <h1 ref="heroHeading" id="hero-heading"
                :class="animateHeroHeading ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-6'"
                class="text-4xl md:text-6xl font-bold leading-tight mb-6 transition-all duration-700 delay-200">
                We Build Powerful Structures That
                <span class="text-orange-500">Stand The Test of Time</span>
            </h1>

            <p ref="heroParagraph" id="hero-paragraph"
                :class="animateHeroParagraph ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-6'"
                class="text-gray-300 text-lg mb-8 leading-relaxed transition-all duration-700 delay-400">
                From commercial buildings to infrastructure projects, we deliver high-quality solutions with precision,
                safety,
                and unmatched expertise.
            </p>

            <div class="flex flex-col sm:flex-row gap-4 justify-center md:justify-center">
                <a href="#consultation"
                    class="px-8 py-3 rounded-lg bg-orange-500 hover:bg-orange-600 text-white font-semibold shadow-md transition duration-300">
                    Get free consultaion
                </a>

                <a href="#projects"
                    class="px-8 py-3 rounded-lg border border-gray-600 text-gray-300 hover:bg-white/5 transition duration-300">
                    View Projects
                </a>
            </div>


            <!-- Google Map Embed -->

        </div>
    </section>

    <!-- ================= ABOUT ================= -->
    <section id="about" class="relative bg-black text-white py-28 overflow-hidden">

        <!-- Subtle Construction Grid Background -->
        <svg class="absolute inset-0 w-full h-full opacity-[0.04]" xmlns="http://www.w3.org/2000/svg"
            preserveAspectRatio="xMidYMid slice">
            <defs>
                <pattern id="constructionGrid" width="60" height="60" patternUnits="userSpaceOnUse">
                    <path d="M60 0 L0 0 0 60" fill="none" stroke="#f97316" stroke-width="0.6" />
                </pattern>
            </defs>
            <rect width="100%" height="100%" fill="url(#constructionGrid)" />
        </svg>

        <div class="relative max-w-7xl mx-auto px-6 md:px-12 flex flex-col md:flex-row items-center gap-16">

            <!-- Image -->
            <div class="md:w-1/2">
                <img src="https://i.pinimg.com/736x/0b/9c/5e/0b9c5eecc4df2eb1ed1db6aec9537a53.jpg"
                    alt="Construction Work" class="w-full max-w-lg mx-auto rounded-2xl shadow-xl " />
            </div>

            <!-- Text Content -->
            <div class="md:w-1/2 bg-white/5 backdrop-blur-md rounded-2xl p-8 md:p-12 space-y-8">

                <h2 class="text-3xl md:text-4xl font-bold text-orange-500">
                    About Rubiknows Engineering & Construction
                </h2>

                <p class="text-gray-300 text-lg leading-relaxed">
                    For over a decade, we have delivered high-performance engineering
                    and infrastructure solutions through technical precision,
                    innovation, and strict safety standards.
                </p>

                <!-- Highlights -->
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-6">

                    <!-- Item -->
                    <div class="flex items-start gap-4">
                        <div class="w-6 h-6 text-orange-500">
                            <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24">
                                <path d="M3 21h18M5 21V7l7-4 7 4v14" />
                            </svg>
                        </div>
                        <p class="text-gray-300 text-sm">
                            Architectural, Civil & Electrical expertise.
                        </p>
                    </div>

                    <div class="flex items-start gap-4">
                        <div class="w-6 h-6 text-orange-500">
                            <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24">
                                <path d="M12 2l4 8H8l4-8z" />
                            </svg>
                        </div>
                        <p class="text-gray-300 text-sm">
                            Sustainable & eco-conscious construction practices.
                        </p>
                    </div>

                    <div class="flex items-start gap-4">
                        <div class="w-6 h-6 text-orange-500">
                            <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24">
                                <path d="M5 13l4 4L19 7" />
                            </svg>
                        </div>
                        <p class="text-gray-300 text-sm">
                            Precision-driven execution & quality control.
                        </p>
                    </div>

                    <div class="flex items-start gap-4">
                        <div class="w-6 h-6 text-orange-500">
                            <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24">
                                <path d="M13 3v10h8" />
                            </svg>
                        </div>
                        <p class="text-gray-300 text-sm">
                            Innovative and cost-efficient project delivery.
                        </p>
                    </div>

                </div>

                <!-- Minimalist CTA Buttons -->
                <div class="flex flex-col sm:flex-row gap-4 pt-6">

                    <!-- Primary -->
                    <button
                        class="cursor-pointer bg-orange-500 text-black font-semibold px-8 py-3 rounded-md hover:bg-orange-600 transition duration-300">
                        Learn More
                    </button>

                    <!-- Minimal Secondary -->
                    <button
                        class=" cursor-pointer text-orange-500 font-semibold px-8 py-3 rounded-md border border-orange-500 hover:bg-orange-500 hover:text-black transition duration-300">
                        Request Quote
                    </button>

                </div>

            </div>
        </div>
    </section>
    <!-- ================= SERVICES ================= -->
    <section id="services" class="relative bg-black text-white py-28 overflow-hidden">

        <!-- Subtle Orange Blueprint Grid -->
        <div class="absolute inset-0 opacity-[0.04]" style="background-image: linear-gradient(to right, #f97316 1px, transparent 1px),
               linear-gradient(to bottom, #f97316 1px, transparent 1px);
               background-size: 50px 50px;">
        </div>

        <div class="relative max-w-7xl mx-auto px-6 md:px-12">

            <!-- Heading -->
            <div class="text-center mb-16">
                <h2 class="text-4xl md:text-5xl font-bold text-orange-500 mb-4">
                    Our Services
                </h2>
                <p class="text-gray-400 max-w-2xl mx-auto text-lg">
                    High-performance engineering and construction solutions built with strength, precision, and
                    reliability.
                </p>
            </div>

            <!-- Services Grid -->
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-10">

                <!-- CARD 1 -->
                <div
                    class=" cursor-pointer bg-orange-500/5 rounded-2xl p-8 transition duration-300 hover:bg-orange-500/10 hover:-translate-y-1">
                    <div class="w-12 h-12 text-orange-500 mb-6">
                        <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24">
                            <path d="M3 21h18M5 21V7l7-4 7 4v14" />
                        </svg>
                    </div>
                    <h3 class="text-xl font-semibold mb-4 text-white">Architectural Design</h3>
                    <p class="text-gray-400 text-sm">Structural and functional designs engineered for durability.</p>
                </div>

                <!-- CARD 2 -->
                <div
                    class=" cursor-pointer bg-orange-500/5 rounded-2xl p-8 transition duration-300 hover:bg-orange-500/10 hover:-translate-y-1">
                    <div class="w-12 h-12 text-orange-500 mb-6">
                        <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24">
                            <path d="M14.7 6.3l3 3m-9.4 9.4l9.4-9.4M3 21h6" />
                        </svg>
                    </div>
                    <h3 class="text-xl font-semibold mb-4 text-white">Engineering Services</h3>
                    <p class="text-gray-400 text-sm">Comprehensive civil, structural, and mechanical expertise.</p>
                </div>

                <!-- CARD 3 -->
                <div
                    class=" cursor-pointer bg-orange-500/5 rounded-2xl p-8 transition duration-300 hover:bg-orange-500/10 hover:-translate-y-1">
                    <div class="w-12 h-12 text-orange-500 mb-6">
                        <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24">
                            <path d="M3 3h18v18H3z" />
                        </svg>
                    </div>
                    <h3 class="text-xl font-semibold mb-4 text-white">Construction Management</h3>
                    <p class="text-gray-400 text-sm">Efficient project delivery with strict safety standards.</p>
                </div>

                <!-- Hidden Cards -->
                <template v-if="showMore">

                    <div
                        class=" cursor-pointer bg-orange-500/5 rounded-2xl p-8 transition duration-300 hover:bg-orange-500/10 hover:-translate-y-1">
                        <div class="w-12 h-12 text-orange-500 mb-6">
                            <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24">
                                <path d="M12 8v8m-4-4h8" />
                            </svg>
                        </div>
                        <h3 class="text-xl font-semibold mb-4 text-white">Consulting</h3>
                        <p class="text-gray-400 text-sm">Planning, budgeting, and feasibility expertise.</p>
                    </div>

                    <div
                        class=" cursor-pointer bg-orange-500/5 rounded-2xl p-8 transition duration-300 hover:bg-orange-500/10 hover:-translate-y-1">
                        <div class="w-12 h-12 text-orange-500 mb-6">
                            <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24">
                                <path d="M12 2l4 8H8l4-8z" />
                            </svg>
                        </div>
                        <h3 class="text-xl font-semibold mb-4 text-white">Sustainability</h3>
                        <p class="text-gray-400 text-sm">Green construction and energy-efficient solutions.</p>
                    </div>

                    <div
                        class=" cursor-pointer bg-orange-500/5 rounded-2xl p-8 transition duration-300 hover:bg-orange-500/10 hover:-translate-y-1">
                        <div class="w-12 h-12 text-orange-500 mb-6">
                            <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24">
                                <path d="M9 17v-6h6v6" />
                            </svg>
                        </div>
                        <h3 class="text-xl font-semibold mb-4 text-white">Interior Solutions</h3>
                        <p class="text-gray-400 text-sm">Functional finishing and modern construction detailing.</p>
                    </div>

                </template>

            </div>

            <!-- View More Button -->
            <div class="text-center mt-16">
                <button @click="showMore = !showMore"
                    class=" cursor-pointer bg-orange-500 hover:bg-orange-600 text-black font-semibold px-8 py-3 rounded-md transition duration-300 shadow-md">
                    {{ showMore ? 'Show Less' : 'View More Services' }}
                </button>
            </div>

        </div>
    </section>


    <!-- ================= PROJECTS ================= -->
    <section id="projects" ref="projectsSection" class="relative bg-black text-white py-24 overflow-hidden">

        <!-- Subtle Engineering Grid Background -->
        <svg class="absolute inset-0 w-full h-full opacity-10" xmlns="http://www.w3.org/2000/svg"
            preserveAspectRatio="xMidYMid slice">
            <defs>
                <pattern id="projectsGrid" width="60" height="60" patternUnits="userSpaceOnUse">
                    <path d="M60 0 L0 0 0 60" fill="none" stroke="#FFA500" stroke-width="0.5" />
                    <circle cx="30" cy="30" r="2" fill="#FFA500" />
                </pattern>
            </defs>
            <rect width="100%" height="100%" fill="url(#projectsGrid)" />
        </svg>

        <div class="relative max-w-7xl mx-auto px-6 md:px-12">

            <!-- Header -->
            <div class="text-center mb-12">
                <h2 class="text-3xl md:text-4xl font-bold text-orange-500">Our Projects</h2>
                <p class="text-gray-300 mt-4 max-w-2xl mx-auto">
                    High-quality engineering and construction projects delivered with precision, safety, and innovation.
                </p>
            </div>

            <!-- Projects Grid -->
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
                <template v-for="(project, index) in projects" :key="index">
                    <div v-if="index < 3 || showMore"
                        class="group relative overflow-hidden rounded-2xl cursor-pointer transform transition duration-500 hover:scale-105"
                        @click="openModal(project)">

                        <img :src="project.image" :alt="project.title"
                            class="w-full h-64 object-cover transition-transform duration-500 group-hover:scale-110" />

                        <div
                            class="absolute inset-0 bg-black/50 backdrop-blur-sm opacity-0 group-hover:opacity-100 transition-opacity duration-500 flex flex-col items-center justify-center px-6 text-center">

                            <!-- Minimalist SVG Icon -->
                            <div class="w-10 h-10 text-orange-500 mb-3">
                                <svg fill="none" stroke="currentColor" stroke-width="1.8" viewBox="0 0 24 24">
                                    <path v-html="project.iconPath" />
                                </svg>
                            </div>

                            <h3 class="text-xl font-bold text-orange-500">{{ project.title }}</h3>
                            <p class="text-gray-300 mt-2 text-sm">{{ project.description }}</p>
                        </div>
                    </div>
                </template>
            </div>

            <!-- Show More Button -->
            <div class="mt-12 text-center">
                <button @click="toggleProjects"
                    class="cursor-pointer bg-orange-500 hover:bg-orange-600 text-black font-semibold px-8 py-3 rounded-md transition duration-300">
                    {{ showMore ? 'Show Less' : 'View More Projects' }}
                </button>
            </div>

            <!-- Modal / Lightbox -->
            <!-- Modal / Lightbox -->
            <transition name="fade-scale">
                <div v-if="modalProject"
                    class="fixed inset-0 z-50 bg-black/90 flex items-center justify-center p-4 backdrop-blur-sm">

                    <div
                        class="relative max-w-4xl w-full bg-black rounded-xl overflow-hidden transition-all duration-500 scale-95 border border-orange-500/30">

                        <!-- Close Button -->
                        <button @click="closeModal"
                            class="absolute top-3 right-2 text-orange-500 bg-orange-300 rounded-full py-1 px-2 font-bold text-4xl hover:text-white transition z-50">&times;</button>

                        <!-- Back / Next Buttons -->
                        <button @click="prevProject"
                            class="absolute left-4 top-1/2 transform -translate-y-1/2 font-bold text-orange-500 text-6xl hover:text-white transition z-50">
                            &#8592;
                        </button>
                        <button @click="nextProject"
                            class="absolute right-4 top-1/2 transform -translate-y-1/2 font-bold text-orange-500 text-6xl hover:text-white transition z-50">
                            &#8594;
                        </button>

                        <!-- Modal Image -->
                        <div class="relative w-full h-96 md:h-[28rem] overflow-hidden">
                            <img :src="modalProject.image" :alt="modalProject.title"
                                class="w-full h-full object-cover transition-transform duration-500 hover:scale-105" />

                            <!-- Subtle Overlay Grid for Engineering Theme -->
                            <svg class="absolute inset-0 w-full h-full opacity-10" xmlns="http://www.w3.org/2000/svg">
                                <defs>
                                    <pattern id="modalGrid" width="40" height="40" patternUnits="userSpaceOnUse">
                                        <path d="M40 0 L0 0 0 40" fill="none" stroke="#FFA500" stroke-width="0.3" />
                                        <circle cx="20" cy="20" r="1.5" fill="#FFA500" />
                                    </pattern>
                                </defs>
                                <rect width="100%" height="100%" fill="url(#modalGrid)" />
                            </svg>
                        </div>

                        <!-- Modal Text -->
                        <div class="p-6 text-center bg-black/70 backdrop-blur-sm">
                            <h3 class="text-2xl md:text-3xl font-bold text-orange-500">{{ modalProject.title }}</h3>
                            <p class="text-gray-300 mt-2 text-sm md:text-base">{{ modalProject.description }}</p>
                        </div>

                    </div>
                </div>
            </transition>

        </div>
    </section>

    <!-- ================= CONTACT ================= -->
    <section id="contact" ref="contactSection" class="relative bg-black text-white py-20">

        <!-- Subtle Engineering Grid Background -->
        <svg class="absolute inset-0 w-full h-full opacity-10" xmlns="http://www.w3.org/2000/svg"
            preserveAspectRatio="xMidYMid slice">
            <defs>
                <pattern id="contactGrid" width="60" height="60" patternUnits="userSpaceOnUse">
                    <path d="M60 0 L0 0 0 60" fill="none" stroke="#FFA500" stroke-width="0.5" />
                    <circle cx="30" cy="30" r="2" fill="#FFA500" />
                </pattern>
            </defs>
            <rect width="100%" height="100%" fill="url(#contactGrid)" />
        </svg>

        <div class="relative z-10 max-w-2xl mx-auto px-6 md:px-12">

            <!-- Heading -->
            <div class="text-center mb-12">
                <h2 class="text-3xl md:text-4xl font-bold text-orange-500">Get In Touch</h2>
                <p class="text-gray-300 mt-4 max-w-xl mx-auto">
                    Have a project in mind? Reach out to us and let's discuss how we can bring it to life!
                </p>
            </div>

            <!-- Contact Form -->
            <form class="bg-gray-900/80 backdrop-blur-md p-8 rounded-3xl shadow-lg space-y-6">
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <input type="text" placeholder="Your Name"
                        class="w-full px-4 py-3 rounded-md bg-gray-800 text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-orange-500 transition"
                        required />
                    <input type="email" placeholder="Your Email"
                        class="w-full px-4 py-3 rounded-md bg-gray-800 text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-orange-500 transition"
                        required />
                </div>

                <input type="text" placeholder="Subject"
                    class="w-full px-4 py-3 rounded-md bg-gray-800 text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-orange-500 transition"
                    required />

                <textarea placeholder="Your Message" rows="5"
                    class="w-full px-4 py-3 rounded-md bg-gray-800 text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-orange-500 transition"
                    required></textarea>

                <div class="text-center">
                    <button type="submit"
                        class=" cursor-pointer bg-orange-500 hover:bg-orange-600 text-black font-semibold px-8 py-3 rounded-full shadow-md transition duration-300 hover:scale-105">
                        Send Message
                    </button>
                </div>
            </form>

        </div>
    </section>

    <section id="consultation"
        class="relative w-full min-h-screen flex items-center justify-center overflow-hidden bg-gradient-to-br from-gray-950 via-gray-900 to-gray-800">

        <!-- Background Image & Overlay -->
        <div class="absolute inset-0">
            <img src="https://i.pinimg.com/736x/75/de/07/75de0749aa17d31912274fc15ba4545e.jpg"
                class="w-full h-full object-cover opacity-20" />
            <div class="absolute inset-0 bg-black/70"></div>
        </div>

        <!-- Soft Engineering Glow -->
        <div class="absolute top-24 left-24 w-72 h-72 bg-orange-500/10 rounded-full blur-3xl"></div>
        <div class="absolute bottom-24 right-24 w-80 h-80 bg-gray-600/10 rounded-full blur-3xl"></div>

        <!-- Content Grid -->
        <div class="relative z-10 max-w-7xl w-full px-6 md:px-12 grid md:grid-cols-2 gap-16 items-center">

            <!-- Text Section -->
            <div class="space-y-8 text-center md:text-left">

                <div
                    class="inline-block px-4 py-1 text-sm tracking-widest text-orange-400 uppercase bg-orange-500/10 rounded-full backdrop-blur-sm">
                    Engineering Excellence
                </div>

                <h1 class="text-4xl md:text-6xl font-bold leading-tight text-white">
                    Free Consultation <br>
                    <span class="text-orange-400">Precision Engineering Solutions</span>
                </h1>

                <p class="text-gray-300 text-lg max-w-xl mx-auto md:mx-0">
                    Schedule a free consultation with our experts to discuss your construction or engineering project.
                    We provide innovative, safe, and reliable solutions tailored to your needs.
                </p>

                <div class="flex flex-col sm:flex-row gap-4 justify-center md:justify-start">
                    <a href="#contact"
                        class="px-8 py-3 rounded-lg bg-white text-black font-semibold shadow-md hover:bg-gray-200 transition duration-300">
                        Request Consultation
                    </a>

                    <a href="#projects"
                        class="px-8 py-3 rounded-lg border border-gray-600 text-gray-300 hover:bg-white/5 transition duration-300">
                        View Projects
                    </a>
                </div>



            </div>

            <!-- Map Section -->
            <div class="relative w-full h-96 md:h-[480px] rounded-2xl overflow-hidden shadow-xl">
                <iframe
                    src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3960.540561827117!2d125.8169435!3d7.4508667!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x32f953b3b7d922c3%3A0x21927934c5a5b49c!2sRUBIKNOWS%20Engineering%20and%20Construction!5e0!3m2!1sen!2sph!4v1708959912345!5m2!1sen!2sph"
                    class="w-full h-full border-0" allowfullscreen="" loading="lazy"
                    referrerpolicy="no-referrer-when-downgrade"></iframe>
            </div>

        </div>
    </section>
    <!-- Add this to your Tailwind config if using Tailwind JIT or arbitrary values -->

    <footer class="bg-black text-gray-300 py-10 md:py-16 relative overflow-hidden">

        <!-- Subtle SVG background -->
        <svg class="absolute inset-0 w-full h-full opacity-5 pointer-events-none" xmlns="http://www.w3.org/2000/svg"
            preserveAspectRatio="xMidYMid slice">
            <defs>
                <pattern id="footerGrid" width="50" height="50" patternUnits="userSpaceOnUse">
                    <path d="M50 0 L0 0 0 50" fill="none" stroke="#FFA500" stroke-width="0.3" />
                </pattern>
            </defs>
            <rect width="100%" height="100%" fill="url(#footerGrid)" />
        </svg>

        <div class="relative max-w-7xl mx-auto px-5 md:px-12 
                grid grid-cols-1 md:grid-cols-3 
                gap-8 md:gap-12 text-center md:text-left">

            <!-- About -->
            <div class="space-y-3 md:space-y-4">
                <h3 class="text-lg md:text-xl font-bold text-orange-500">
                    Rubiknows Engineering & Construction
                </h3>

                <p class="text-gray-400 text-xs md:text-sm leading-relaxed max-w-sm mx-auto md:mx-0">
                    Delivering high-quality engineering and construction solutions with precision,
                    innovation, and safety.
                </p>

                <div class="flex justify-center md:justify-start space-x-4 pt-1">
                    <!-- Social Icons -->
                    <a href="#" class="hover:text-orange-500 transition transform hover:scale-110">
                        <svg class="w-4 h-4 md:w-5 md:h-5" fill="currentColor" viewBox="0 0 24 24">
                            <path
                                d="M24 4.56v15.92c0 .55-.45 1-1 1h-22c-.55 0-1-.45-1-1v-15.92c0-.55.45-1 1-1h22c.55 0 1 .45 1 1zm-4.5 0h-1.5v1.5h1.5v-1.5zm-2 0h-1.5v1.5h1.5v-1.5zm-2 0h-1.5v1.5h1.5v-1.5zm4.5 2.5h-14v14h14v-14z" />
                        </svg>
                    </a>
                    <a href="#" class="hover:text-orange-500 transition transform hover:scale-110">
                        <svg class="w-4 h-4 md:w-5 md:h-5" fill="currentColor" viewBox="0 0 24 24">
                            <path
                                d="M24 4.5v15c0 .828-.672 1.5-1.5 1.5h-21c-.828 0-1.5-.672-1.5-1.5v-15c0-.828.672-1.5 1.5-1.5h21c.828 0 1.5.672 1.5 1.5zm-9.375 10.875v-5.25l4.5 2.625-4.5 2.625zm9.375-10.875h-21v15h21v-15z" />
                        </svg>
                    </a>
                    <a href="#" class="hover:text-orange-500 transition transform hover:scale-110">
                        <svg class="w-4 h-4 md:w-5 md:h-5" fill="currentColor" viewBox="0 0 24 24">
                            <path
                                d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.956-2.178-1.555-3.594-1.555-2.719 0-4.924 2.206-4.924 4.924 0 .386.044.762.127 1.124-4.092-.205-7.725-2.166-10.157-5.144-.425.73-.668 1.577-.668 2.476 0 1.708.87 3.216 2.188 4.099-.807-.026-1.566-.247-2.229-.616v.062c0 2.385 1.697 4.374 3.95 4.827-.413.112-.849.172-1.296.172-.317 0-.626-.031-.928-.088.627 1.956 2.444 3.379 4.6 3.418-1.68 1.316-3.808 2.101-6.115 2.101-.398 0-.79-.023-1.177-.069 2.179 1.397 4.768 2.211 7.548 2.211 9.054 0 14.01-7.5 14.01-14.01 0-.213-.005-.425-.014-.636.961-.693 1.797-1.562 2.457-2.549z" />
                        </svg>
                    </a>
                </div>
            </div>

            <!-- Quick Links -->
            <div class="space-y-3 md:space-y-4">
                <h3 class="text-lg md:text-xl font-bold text-orange-500">Quick Links</h3>
                <ul class="space-y-1 md:space-y-2 text-gray-400 text-xs md:text-sm">
                    <li><a href="#hero" class="hover:text-orange-500 transition">Home</a></li>
                    <li><a href="#about" class="hover:text-orange-500 transition">About</a></li>
                    <li><a href="#services" class="hover:text-orange-500 transition">Services</a></li>
                    <li><a href="#projects" class="hover:text-orange-500 transition">Projects</a></li>
                    <li><a href="#contact" class="hover:text-orange-500 transition">Contact</a></li>
                </ul>
            </div>

            <!-- Contact -->
            <div class="space-y-3 md:space-y-4">
                <h3 class="text-lg md:text-xl font-bold text-orange-500">Contact</h3>

                <div class="text-gray-400 text-xs md:text-sm space-y-1 leading-relaxed">
                    <p><span class="text-orange-500 font-medium">Email:</span> rubiknows.ph@gmail.com</p>
                    <p><span class="text-orange-500 font-medium">Phone:</span> +63 956 407 3918</p>
                    <p class="max-w-xs mx-auto md:mx-0">
                        <span class="text-orange-500 font-medium">Address:</span>
                        Barangay Apokon, Tagum City, Davao del Norte
                    </p>
                </div>
            </div>

        </div>

        <!-- Bottom -->
        <div class="mt-8 md:mt-12 border-t border-orange-500/30 pt-4 md:pt-6 
                text-center text-gray-500 text-xs md:text-sm space-y-1">
            <p>&copy; 2026 Rubiknows Engineering & Construction. All rights reserved.</p>
            <a href="https://www.pinterest.com" target="_blank" rel="noopener noreferrer"
                class="text-orange-500 hover:text-orange-400 transition">
                Pinterest
            </a>
        </div>

    </footer>
</template>