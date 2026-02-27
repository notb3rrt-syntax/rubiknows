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
    }
};
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
    <header class="fixed w-full top-0 z-50 backdrop-blur-lg bg-black/60 border-b border-orange-500/20 shadow-lg">
        <nav class="max-w-7xl mx-auto px-6 py-4 flex justify-between items-center">

            <!-- Logo / Brand -->
            <div class="cursor-pointer text-white font-bold text-lg tracking-wide">
                Rubiknows
            </div>

            <!-- Desktop Menu -->
            <ul class="hidden md:flex items-center space-x-10 text-gray-300 font-medium">
                <li><a href="#hero" class="cursor-pointer relative group hover:text-orange-500 transition duration-300">
                        Home
                        <span
                            class="cursor-pointer absolute left-0 -bottom-1 w-0 h-0.5 bg-orange-500 transition-all duration-300 group-hover:w-full"></span>
                    </a></li>

                <li><a href="#about"
                        class="cursor-pointer relative group hover:text-orange-500 transition duration-300">
                        About
                        <span
                            class="cursor-pointer absolute left-0 -bottom-1 w-0 h-0.5 bg-orange-500 transition-all duration-300 group-hover:w-full"></span>
                    </a></li>

                <li><a href="#services"
                        class="cursor-pointer relative group hover:text-orange-500 transition duration-300">
                        Services
                        <span
                            class="cursor-pointer absolute left-0 -bottom-1 w-0 h-0.5 bg-orange-500 transition-all duration-300 group-hover:w-full"></span>
                    </a></li>

                <li><a href="#projects"
                        class="cursor-pointer relative group hover:text-orange-500 transition duration-300">
                        Projects
                        <span
                            class="absolute left-0 -bottom-1 w-0 h-0.5 bg-orange-500 transition-all duration-300 group-hover:w-full"></span>
                    </a></li>

                <li><a href="#contact" class="relative group hover:text-orange-500 transition duration-300">
                        Contact
                        <span
                            class="cursor-pointer absolute left-0 -bottom-1 w-0 h-0.5 bg-orange-500 transition-all duration-300 group-hover:w-full"></span>
                    </a></li>
            </ul>

            <!-- Modern CTA -->
            <div class="hidden md:block">
                <button
                    class="cursor-pointer relative overflow-hidden bg-orange-500 text-black font-semibold px-7 py-2.5 rounded-full transition-all duration-300 hover:scale-105 hover:shadow-[0_0_20px_rgba(249,115,22,0.6)]">
                    <span class="relative z-10">Get a Free Quote</span>
                    <span class="absolute inset-0 bg-orange-400 opacity-0 hover:opacity-20 transition"></span>
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
        <div v-if="isOpen"
            class="md:hidden backdrop-blur-lg bg-black/80 border-t border-orange-500/20 px-6 py-6 space-y-6 text-gray-300 animate-fadeIn">
            <a href="#hero" class="cursor-pointer block hover:text-orange-500 transition">Home</a>
            <a href="#about" class="cursor-pointer block hover:text-orange-500 transition">About</a>
            <a href="#services" class="cursor-pointer block hover:text-orange-500 transition">Services</a>
            <a href="#projects" class="block hover:text-orange-500 transition">Projects</a>
            <a href="#contact" class="cursor-pointer block hover:text-orange-500 transition">Contact</a>

            <button
                class="w-full bg-orange-500 hover:bg-orange-600 text-black font-semibold px-5 py-3 rounded-full transition-all duration-300 hover:scale-105 hover:shadow-[0_0_15px_rgba(249,115,22,0.6)]">
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

            <div ref="heroButtons" id="hero-buttons"
                :class="animateHeroButtons ? 'opacity-100 translate-y-0' : 'opacity-0 translate-y-6'"
                class="flex flex-col sm:flex-row gap-4 justify-center transition-all duration-700 delay-600">
                <button
                    class="cursor-pointer bg-orange-500 hover:bg-orange-600 text-black font-semibold px-8 py-3 rounded-md transition duration-300">
                    Get Free Consultation
                </button>
                <button
                    class="cursor-pointer border border-orange-500 text-orange-500 hover:bg-orange-500 hover:text-black font-semibold px-8 py-3 rounded-md transition duration-300">
                    View Our Projects
                </button>
            </div>

            <!-- Google Map Embed -->
            <div
                class="max-w-lg mx-auto bg-white/5 backdrop-blur-lg border border-orange-500/30 rounded-2xl p-6 shadow-xl mt-10">

                <h2 class="text-xl font-semibold mb-4 text-orange-500">
                    Our Location:
                </h2>

                <div class="w-full h-56 rounded-xl overflow-hidden border border-orange-500/40 ">
                    <iframe class="w-full h-full"
                        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3960.540561827117!2d125.8169435!3d7.4508667!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x32f953b3b7d922c3%3A0x21927934c5a5b49c!2sRUBIKNOWS%20Engineering%20and%20Construction!5e0!3m2!1sen!2sph!4v1708959912345!5m2!1sen!2sph"
                        allowfullscreen loading="lazy" referrerpolicy="no-referrer-when-downgrade">
                    </iframe>
                </div>

            </div>
        </div>
    </section>

    <!-- ================= ABOUT ================= -->
    <section id="about" class="relative bg-black text-white py-28 overflow-hidden">

        <!-- Subtle Construction Grid Background -->
        <svg class="absolute inset-0 w-full h-full opacity-5" xmlns="http://www.w3.org/2000/svg"
            preserveAspectRatio="xMidYMid slice">
            <defs>
                <pattern id="constructionGrid" width="60" height="60" patternUnits="userSpaceOnUse">
                    <path d="M60 0 L0 0 0 60" fill="none" stroke="#FFA500" stroke-width="0.5" />
                </pattern>
            </defs>
            <rect width="100%" height="100%" fill="url(#constructionGrid)" />
        </svg>

        <div class="relative max-w-7xl mx-auto px-6 md:px-12 flex flex-col md:flex-row items-center gap-16">

            <!-- Image -->
            <div class="md:w-1/2">
                <img src="https://i.pinimg.com/736x/0b/9c/5e/0b9c5eecc4df2eb1ed1db6aec9537a53.jpg"
                    alt="Construction Work"
                    class="w-full max-w-lg mx-auto rounded-3xl shadow-2xl transition duration-500 hover:scale-105 hover:shadow-[0_0_40px_rgba(249,115,22,0.25)]" />
            </div>

            <!-- Text Content -->
            <div
                class="md:w-1/2 bg-white/5 backdrop-blur-lg border border-orange-500/20 rounded-3xl p-8 md:p-12 space-y-8 shadow-xl">

                <h2 class="text-3xl md:text-4xl font-extrabold text-orange-500">
                    About Rubiknows Engineering & Construction
                </h2>

                <p class="text-gray-300 text-lg leading-relaxed">
                    For over a decade, Rubiknows Engineering & Construction has delivered
                    world-class engineering and infrastructure solutions. Our team combines
                    deep technical expertise, innovative thinking, and uncompromising
                    safety standards to bring every project to life.
                </p>

                <!-- Highlights -->
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-6">

                    <div class="flex items-start gap-4">
                        <div
                            class="w-8 h-8 flex items-center justify-center rounded-full bg-orange-500/20 text-orange-500">
                            ✓
                        </div>
                        <p class="text-gray-300 text-sm">
                            Architectural, Civil & Electrical expertise.
                        </p>
                    </div>

                    <div class="flex items-start gap-4">
                        <div
                            class="w-8 h-8 flex items-center justify-center rounded-full bg-orange-500/20 text-orange-500">
                            🌱
                        </div>
                        <p class="text-gray-300 text-sm">
                            Sustainable & eco-friendly construction practices.
                        </p>
                    </div>

                    <div class="flex items-start gap-4">
                        <div
                            class="w-8 h-8 flex items-center justify-center rounded-full bg-orange-500/20 text-orange-500">
                            ⭐
                        </div>
                        <p class="text-gray-300 text-sm">
                            Precision-driven execution & client satisfaction.
                        </p>
                    </div>

                    <div class="flex items-start gap-4">
                        <div
                            class="w-8 h-8 flex items-center justify-center rounded-full bg-orange-500/20 text-orange-500">
                            ⚡
                        </div>
                        <p class="text-gray-300 text-sm">
                            Innovative, functional & cost-efficient designs.
                        </p>
                    </div>

                </div>

                <!-- CTA Buttons -->
                <div class="flex flex-col sm:flex-row gap-5 pt-4">

                    <button
                        class="bg-orange-500 hover:bg-orange-600 text-black font-semibold px-8 py-3 rounded-full transition-all duration-300 hover:scale-105 hover:shadow-[0_0_20px_rgba(249,115,22,0.6)]">
                        Learn More
                    </button>

                    <button
                        class="border border-orange-500 text-orange-500 hover:bg-orange-500 hover:text-black font-semibold px-8 py-3 rounded-full transition-all duration-300 hover:scale-105">
                        Request Quote
                    </button>

                </div>

            </div>
        </div>
    </section>

    <!-- ================= SERVICES ================= -->
    <section id="services" class="relative bg-black text-white py-28 overflow-hidden">

        <div class="max-w-7xl mx-auto px-6 md:px-12">

            <!-- Heading -->
            <div class="text-center mb-16">
                <h2 class="text-4xl md:text-5xl font-extrabold text-orange-500 mb-4">
                    Our Services
                </h2>
                <p class="text-gray-400 max-w-2xl mx-auto text-lg">
                    Comprehensive architectural, engineering, and construction solutions
                    delivered with precision and innovation.
                </p>
            </div>

            <!-- Services Grid -->
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">

                <!-- 1 -->
                <div
                    class="group relative bg-white/5 backdrop-blur-lg border border-orange-500/20 rounded-3xl p-8 transition-all duration-500 hover:-translate-y-3 hover:shadow-[0_0_40px_rgba(249,115,22,0.25)]">
                    <div
                        class="w-14 h-14 flex items-center justify-center rounded-xl bg-orange-500/20 text-orange-500 mb-6 group-hover:bg-orange-500 group-hover:text-black transition">
                        🏗️</div>
                    <h3 class="text-xl font-bold mb-4 group-hover:text-orange-400 transition">Architectural Design</h3>
                    <p class="text-gray-400 text-sm">Creative and functional architectural solutions for residential and
                        commercial developments.</p>
                </div>

                <!-- 2 -->
                <div
                    class="group relative bg-white/5 backdrop-blur-lg border border-orange-500/20 rounded-3xl p-8 transition-all duration-500 hover:-translate-y-3 hover:shadow-[0_0_40px_rgba(249,115,22,0.25)]">
                    <div
                        class="w-14 h-14 flex items-center justify-center rounded-xl bg-orange-500/20 text-orange-500 mb-6 group-hover:bg-orange-500 group-hover:text-black transition">
                        ⚙️</div>
                    <h3 class="text-xl font-bold mb-4 group-hover:text-orange-400 transition">Engineering Services</h3>
                    <p class="text-gray-400 text-sm">Civil, mechanical, electrical and structural engineering solutions
                        with precision and compliance.</p>
                </div>

                <!-- 3 -->
                <div
                    class="group relative bg-white/5 backdrop-blur-lg border border-orange-500/20 rounded-3xl p-8 transition-all duration-500 hover:-translate-y-3 hover:shadow-[0_0_40px_rgba(249,115,22,0.25)]">
                    <div
                        class="w-14 h-14 flex items-center justify-center rounded-xl bg-orange-500/20 text-orange-500 mb-6 group-hover:bg-orange-500 group-hover:text-black transition">
                        🏢</div>
                    <h3 class="text-xl font-bold mb-4 group-hover:text-orange-400 transition">Construction Management
                    </h3>
                    <p class="text-gray-400 text-sm">End-to-end project management ensuring timely delivery, safety, and
                        quality standards.</p>
                </div>

                <!-- 4 -->
                <div
                    class="group relative bg-white/5 backdrop-blur-lg border border-orange-500/20 rounded-3xl p-8 transition-all duration-500 hover:-translate-y-3 hover:shadow-[0_0_40px_rgba(249,115,22,0.25)]">
                    <div
                        class="w-14 h-14 flex items-center justify-center rounded-xl bg-orange-500/20 text-orange-500 mb-6 group-hover:bg-orange-500 group-hover:text-black transition">
                        📊</div>
                    <h3 class="text-xl font-bold mb-4 group-hover:text-orange-400 transition">Consulting Services</h3>
                    <p class="text-gray-400 text-sm">Professional consulting for planning, cost estimation, and
                        feasibility studies.</p>
                </div>

                <!-- 5 -->
                <div
                    class="group relative bg-white/5 backdrop-blur-lg border border-orange-500/20 rounded-3xl p-8 transition-all duration-500 hover:-translate-y-3 hover:shadow-[0_0_40px_rgba(249,115,22,0.25)]">
                    <div
                        class="w-14 h-14 flex items-center justify-center rounded-xl bg-orange-500/20 text-orange-500 mb-6 group-hover:bg-orange-500 group-hover:text-black transition">
                        🌱</div>
                    <h3 class="text-xl font-bold mb-4 group-hover:text-orange-400 transition">Sustainability Solutions
                    </h3>
                    <p class="text-gray-400 text-sm">Eco-friendly construction practices that reduce environmental
                        impact and energy usage.</p>
                </div>

                <!-- 6 -->
                <div
                    class="group relative bg-white/5 backdrop-blur-lg border border-orange-500/20 rounded-3xl p-8 transition-all duration-500 hover:-translate-y-3 hover:shadow-[0_0_40px_rgba(249,115,22,0.25)]">
                    <div
                        class="w-14 h-14 flex items-center justify-center rounded-xl bg-orange-500/20 text-orange-500 mb-6 group-hover:bg-orange-500 group-hover:text-black transition">
                        🧪</div>
                    <h3 class="text-xl font-bold mb-4 group-hover:text-orange-400 transition">Technical Services</h3>
                    <p class="text-gray-400 text-sm">Scientific and technical services including NEC engineering and
                        compliance solutions.</p>
                </div>

                <!-- 7 -->
                <div
                    class="group relative bg-white/5 backdrop-blur-lg border border-orange-500/20 rounded-3xl p-8 transition-all duration-500 hover:-translate-y-3 hover:shadow-[0_0_40px_rgba(249,115,22,0.25)]">
                    <div
                        class="w-14 h-14 flex items-center justify-center rounded-xl bg-orange-500/20 text-orange-500 mb-6 group-hover:bg-orange-500 group-hover:text-black transition">
                        📐</div>
                    <h3 class="text-xl font-bold mb-4 group-hover:text-orange-400 transition">Project Feasibility</h3>
                    <p class="text-gray-400 text-sm">In-depth analysis of project viability, budgeting, and strategic
                        planning for smart investments.</p>
                </div>

                <!-- 8 -->
                <div
                    class="group relative bg-white/5 backdrop-blur-lg border border-orange-500/20 rounded-3xl p-8 transition-all duration-500 hover:-translate-y-3 hover:shadow-[0_0_40px_rgba(249,115,22,0.25)]">
                    <div
                        class="w-14 h-14 flex items-center justify-center rounded-xl bg-orange-500/20 text-orange-500 mb-6 group-hover:bg-orange-500 group-hover:text-black transition">
                        🛋️</div>
                    <h3 class="text-xl font-bold mb-4 group-hover:text-orange-400 transition">Interior Design</h3>
                    <p class="text-gray-400 text-sm">Modern, functional, and aesthetic interior solutions for
                        residential and commercial spaces.</p>
                </div>

            </div>

            <!-- Bottom CTA -->
            <div class="text-center mt-20">
                <h3 class="text-2xl font-semibold mb-6">
                    Ready to Start Your Project?
                </h3>

                <button
                    class="bg-orange-500 hover:bg-orange-600 text-black font-semibold px-10 py-4 rounded-full transition-all duration-300 hover:scale-105 hover:shadow-[0_0_25px_rgba(249,115,22,0.6)]">
                    Request a Free Consultation
                </button>
            </div>

        </div>
    </section>


    <!-- ================= PROJECTS ================= -->
    <section id="projects" ref="projectsSection"
        class="relative bg-black text-white py-24 transition-all duration-700 overflow-hidden">

        <!-- Construction/Engineering SVG background -->
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
                    We take pride in delivering high-quality projects that combine innovation, safety, and durability.
                </p>
            </div>

            <!-- Projects Grid -->
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">

                <!-- Example Project Card -->
                <div
                    class="group relative overflow-hidden rounded-2xl shadow-2xl cursor-pointer transform transition duration-500 hover:scale-105 hover:shadow-3xl">
                    <img src="https://i.pinimg.com/736x/cd/43/59/cd4359eb5b895ce4cda433d55de3d608.jpg"
                        alt="Commercial Building"
                        class="w-full h-64 object-cover transition-transform duration-500 group-hover:scale-110" />
                    <div
                        class="absolute inset-0 bg-black/50 backdrop-blur-sm bg-opacity-60 opacity-0 group-hover:opacity-100 transition-opacity duration-500 flex flex-col items-center justify-center px-6 text-center">
                        <h3 class="text-xl font-bold text-orange-500">Commercial Building</h3>
                        <p class="text-gray-300 mt-2 text-sm">A modern office complex built with precision and
                            high-quality materials.</p>
                    </div>
                </div>

                <!-- More Project Cards -->
                <div
                    class="group relative overflow-hidden rounded-2xl shadow-2xl cursor-pointer transform transition duration-500 hover:scale-105 hover:shadow-3xl">
                    <img src="https://i.pinimg.com/1200x/2b/a9/95/2ba995140fe081b838357573ca1232b4.jpg"
                        alt="Residential Complex"
                        class="w-full h-64 object-cover bg-center transition-transform duration-500 group-hover:scale-110" />
                    <div
                        class="absolute inset-0 bg-black/50 backdrop-blur-sm bg-opacity-60 opacity-0 group-hover:opacity-100 transition-opacity duration-500 flex flex-col items-center justify-center px-6 text-center">
                        <h3 class="text-xl font-bold text-orange-500">Residential Complex</h3>
                        <p class="text-gray-300 mt-2 text-sm">A sustainable residential project designed for comfort and
                            safety.</p>
                    </div>
                </div>

                <div
                    class="group relative overflow-hidden rounded-2xl shadow-2xl cursor-pointer transform transition duration-500 hover:scale-105 hover:shadow-3xl">
                    <img src="https://i.pinimg.com/1200x/30/0b/95/300b9516d1f7344d100fe03aba3d2859.jpg"
                        alt="Industrial Facility"
                        class="w-full h-64 object-cover transition-transform duration-500 group-hover:scale-110" />
                    <div
                        class="absolute inset-0 bg-black/50 backdrop-blur-sm bg-opacity-60 opacity-0 group-hover:opacity-100 transition-opacity duration-500 flex flex-col items-center justify-center px-6 text-center">
                        <h3 class="text-xl font-bold text-orange-500">Industrial Facility</h3>
                        <p class="text-gray-300 mt-2 text-sm">A large-scale industrial building built with robust
                            engineering standards.</p>
                    </div>
                </div>

                <!-- Additional Project Cards for a modern grid -->
                <div
                    class="group relative overflow-hidden rounded-2xl shadow-2xl cursor-pointer transform transition duration-500 hover:scale-105 hover:shadow-3xl">
                    <img src="https://i.pinimg.com/736x/3d/c9/c3/3dc9c31e1703ac5a10a04f740203f6ec.jpg"
                        alt="Bridge Construction"
                        class="w-full h-64 object-cover transition-transform duration-500 group-hover:scale-110" />
                    <div
                        class="absolute inset-0 bg-black/50 backdrop-blur-sm bg-opacity-60 opacity-0 group-hover:opacity-100 transition-opacity duration-500 flex flex-col items-center justify-center px-6 text-center">
                        <h3 class="text-xl font-bold text-orange-500">Bridge Construction</h3>
                        <p class="text-gray-300 mt-2 text-sm">Engineering precision for large-scale infrastructure
                            projects.</p>
                    </div>
                </div>

                <div
                    class="group relative overflow-hidden rounded-2xl shadow-2xl cursor-pointer transform transition duration-500 hover:scale-105 hover:shadow-3xl">
                    <img src="https://i.pinimg.com/1200x/1d/1c/08/1d1c0847c6988acf6b965535398c4f00.jpg" alt="Skyscraper"
                        class="w-full h-64 object-cover transition-transform duration-500 group-hover:scale-110" />
                    <div
                        class="absolute inset-0 bg-black/50 backdrop-blur-sm bg-opacity-60 opacity-0 group-hover:opacity-100 transition-opacity duration-500 flex flex-col items-center justify-center px-6 text-center">
                        <h3 class="text-xl font-bold text-orange-500">Skyscraper</h3>
                        <p class="text-gray-300 mt-2 text-sm">Modern high-rise buildings with innovative design
                            solutions.</p>
                    </div>
                </div>

                <div
                    class="group relative overflow-hidden rounded-2xl shadow-2xl cursor-pointer transform transition duration-500 hover:scale-105 hover:shadow-3xl">
                    <img src="https://i.pinimg.com/1200x/44/f3/27/44f327b88768402be361969f9e50c603.jpg"
                        alt="Warehouse Facility"
                        class="w-full h-64 object-cover transition-transform duration-500 group-hover:scale-110" />
                    <div
                        class="absolute inset-0 bg-black/50 backdrop-blur-sm bg-opacity-60 opacity-0 group-hover:opacity-100 transition-opacity duration-500 flex flex-col items-center justify-center px-6 text-center">
                        <h3 class="text-xl font-bold text-orange-500">Warehouse Facility</h3>
                        <p class="text-gray-300 mt-2 text-sm">Efficient industrial spaces built with safety and
                            durability in mind.</p>
                    </div>
                </div>

            </div>

            <!-- CTA Button -->
            <div class="mt-12 text-center">
                <button
                    class="bg-orange-500 hover:bg-orange-600 text-black font-semibold px-8 py-3 rounded-md transition duration-300">
                    View All Projects
                </button>
            </div>

        </div>
    </section>

    <!-- ================= CONTACT ================= -->
    <section id="contact" ref="contactSection" class="bg-black text-white py-20">
        <div class="max-w-4xl mx-auto px-6 md:px-12">
            <div class="text-center mb-12">
                <h2 class="text-3xl md:text-4xl font-bold text-orange-500">Get In Touch</h2>
                <p class="text-gray-300 mt-4 max-w-2xl mx-auto">
                    Have a project in mind? Reach out to us and let's discuss how we can bring it to life!
                </p>
            </div>

            <form class="bg-gray-900 p-8 rounded-lg shadow-lg space-y-6">
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <input type="text" placeholder="Your Name"
                        class="w-full px-4 py-3 rounded-md bg-gray-800 border border-gray-700 text-white focus:outline-none focus:border-orange-500 transition"
                        required />
                    <input type="email" placeholder="Your Email"
                        class="w-full px-4 py-3 rounded-md bg-gray-800 border border-gray-700 text-white focus:outline-none focus:border-orange-500 transition"
                        required />
                </div>

                <input type="text" placeholder="Subject"
                    class="w-full px-4 py-3 rounded-md bg-gray-800 border border-gray-700 text-white focus:outline-none focus:border-orange-500 transition"
                    required />

                <textarea placeholder="Your Message" rows="5"
                    class="w-full px-4 py-3 rounded-md bg-gray-800 border border-gray-700 text-white focus:outline-none focus:border-orange-500 transition"
                    required></textarea>

                <div class="text-center">
                    <button type="submit"
                        class="bg-orange-500 hover:bg-orange-600 text-black font-semibold px-8 py-3 rounded-md transition duration-300">
                        Send Message
                    </button>
                </div>
            </form>


        </div>
    </section>

    <section
        class="relative w-full min-h-screen flex items-center justify-center overflow-hidden bg-gradient-to-br from-gray-950 via-gray-900 to-gray-800">

        <!-- Background Image -->
        <div class="absolute inset-0">
            <img src="https://i.pinimg.com/736x/75/de/07/75de0749aa17d31912274fc15ba4545e.jpg"
                class="w-full h-full object-cover opacity-30" />
            <div class="absolute inset-0 bg-black/70"></div>
        </div>

        <!-- Subtle Professional Glow -->
        <div class="absolute top-24 left-24 w-72 h-72 bg-orange-500/10 rounded-full blur-3xl"></div>
        <div class="absolute bottom-24 right-24 w-80 h-80 bg-gray-600/10 rounded-full blur-3xl"></div>

        <!-- Content -->
        <div class="relative z-10 max-w-7xl w-full px-6 md:px-12 grid md:grid-cols-2 gap-16 items-center">

            <!-- Text Section -->
            <div class="space-y-8 text-center md:text-left">

                <div
                    class="inline-block px-4 py-1 text-sm tracking-widest text-orange-400 uppercase bg-orange-500/10 rounded-full backdrop-blur-sm">
                    Engineering Excellence
                </div>

                <h1 class="text-4xl md:text-6xl font-bold leading-tight text-white">
                    Precision Engineering <br>
                    <span class="text-orange-400">
                        Modern Solutions
                    </span>
                </h1>

                <p class="text-gray-300 text-lg max-w-xl mx-auto md:mx-0">
                    Delivering high-quality engineering and construction solutions
                    with innovation, safety, and reliability at every stage.
                </p>

                <div class="flex flex-col sm:flex-row gap-4 justify-center md:justify-start">
                    <a href="#contact"
                        class="px-8 py-3 rounded-lg bg-orange-500 hover:bg-orange-600 text-white font-semibold shadow-md transition duration-300">
                        Get in Touch
                    </a>

                    <a href="#projects"
                        class="px-8 py-3 rounded-lg border border-gray-600 text-gray-300 hover:bg-white/5 transition duration-300">
                        View Projects
                    </a>
                </div>

                <p class="text-sm text-gray-400 pt-4">
                    Founded by <span class="text-white font-medium">Ruvelyn Robinos</span>
                </p>

            </div>

            <!-- Image Section -->
            <div class="relative flex justify-center">

                <!-- Soft glow behind image -->
                <div class="absolute w-72 h-72 bg-orange-500/10 rounded-full blur-3xl"></div>

                <img :src="maam" alt="Engineering Construction"
                    class="relative w-full max-w-md rounded-2xl shadow-xl transition duration-300 ease-in-out hover:scale-105">
            </div>

        </div>
    </section>
    <!-- Add this to your Tailwind config if using Tailwind JIT or arbitrary values -->

    <footer class="bg-black text-gray-300 py-16 relative overflow-hidden">

        <!-- Optional subtle SVG background pattern -->
        <svg class="absolute inset-0 w-full h-full opacity-5 pointer-events-none" xmlns="http://www.w3.org/2000/svg"
            preserveAspectRatio="xMidYMid slice">
            <defs>
                <pattern id="footerGrid" width="50" height="50" patternUnits="userSpaceOnUse">
                    <path d="M50 0 L0 0 0 50" fill="none" stroke="#FFA500" stroke-width="0.3" />
                </pattern>
            </defs>
            <rect width="100%" height="100%" fill="url(#footerGrid)" />
        </svg>

        <div class="relative max-w-7xl mx-auto px-6 md:px-12 grid grid-cols-1 md:grid-cols-3 gap-12">

            <!-- About / Branding -->
            <div class="space-y-4">
                <h3 class="text-xl font-bold text-orange-500">Rubiknows Engineering & Construction</h3>
                <p class="text-gray-400 text-sm">
                    Delivering high-quality engineering and construction solutions with precision, innovation, and
                    safety.
                </p>
                <div class="flex space-x-4 mt-2">
                    <!-- Social Icons -->
                    <a href="#" class="hover:text-orange-500 transition-transform transform hover:scale-110">
                        <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                            <path
                                d="M24 4.56v15.92c0 .55-.45 1-1 1h-22c-.55 0-1-.45-1-1v-15.92c0-.55.45-1 1-1h22c.55 0 1 .45 1 1zm-4.5 0h-1.5v1.5h1.5v-1.5zm-2 0h-1.5v1.5h1.5v-1.5zm-2 0h-1.5v1.5h1.5v-1.5zm4.5 2.5h-14v14h14v-14z" />
                        </svg>
                    </a>
                    <a href="#" class="hover:text-orange-500 transition-transform transform hover:scale-110">
                        <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                            <path
                                d="M24 4.5v15c0 .828-.672 1.5-1.5 1.5h-21c-.828 0-1.5-.672-1.5-1.5v-15c0-.828.672-1.5 1.5-1.5h21c.828 0 1.5.672 1.5 1.5zm-9.375 10.875v-5.25l4.5 2.625-4.5 2.625zm9.375-10.875h-21v15h21v-15z" />
                        </svg>
                    </a>
                    <a href="#" class="hover:text-orange-500 transition-transform transform hover:scale-110">
                        <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 24 24">
                            <path
                                d="M24 4.557c-.883.392-1.832.656-2.828.775 1.017-.609 1.798-1.574 2.165-2.724-.951.564-2.005.974-3.127 1.195-.897-.956-2.178-1.555-3.594-1.555-2.719 0-4.924 2.206-4.924 4.924 0 .386.044.762.127 1.124-4.092-.205-7.725-2.166-10.157-5.144-.425.73-.668 1.577-.668 2.476 0 1.708.87 3.216 2.188 4.099-.807-.026-1.566-.247-2.229-.616v.062c0 2.385 1.697 4.374 3.95 4.827-.413.112-.849.172-1.296.172-.317 0-.626-.031-.928-.088.627 1.956 2.444 3.379 4.6 3.418-1.68 1.316-3.808 2.101-6.115 2.101-.398 0-.79-.023-1.177-.069 2.179 1.397 4.768 2.211 7.548 2.211 9.054 0 14.01-7.5 14.01-14.01 0-.213-.005-.425-.014-.636.961-.693 1.797-1.562 2.457-2.549z" />
                        </svg>
                    </a>
                </div>
            </div>

            <!-- Quick Links -->
            <div class="space-y-4">
                <h3 class="text-xl font-bold text-orange-500">Quick Links</h3>
                <ul class="space-y-2 text-gray-400 text-sm">
                    <li><a href="#hero" class="hover:text-orange-500 transition">Home</a></li>
                    <li><a href="#about" class="hover:text-orange-500 transition">About</a></li>
                    <li><a href="#services" class="hover:text-orange-500 transition">Services</a></li>
                    <li><a href="#projects" class="hover:text-orange-500 transition">Projects</a></li>
                    <li><a href="#contact" class="hover:text-orange-500 transition">Contact</a></li>
                </ul>
            </div>

            <!-- Contact Info -->
            <div class="space-y-4">
                <h3 class="text-xl font-bold text-orange-500">Contact Us</h3>
                <p class="text-gray-400 text-sm">
                    <span class="font-semibold text-orange-500">Email:</span> rubiknows.ph@gmail.com
                </p>
                <p class="text-gray-400 text-sm">
                    <span class="font-semibold text-orange-500">Phone:</span> +639564073918
                </p>
                <p class="text-gray-400 text-sm">
                    <span class="font-semibold text-orange-500">Address:</span> Stall 6C, JFM Building, City Arcade,
                    Barangay Apokon Tagum, Davao Del Norte, Philippines
                </p>
            </div>

        </div>

        <!-- Footer Bottom -->
        <div class="mt-12 border-t border-orange-500/30 pt-6 text-center text-gray-500 text-sm space-y-1">
            <p>&copy; 2026 Rubiknows Engineering & Construction. All rights reserved.</p>
            <p>
                <a href="https://www.pinterest.com" target="_blank" rel="noopener noreferrer"
                    class="text-orange-500 hover:text-orange-400 transition">Pinterest</a>
            </p>
        </div>
    </footer>
</template>