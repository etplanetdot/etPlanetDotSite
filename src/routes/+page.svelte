<script lang="ts">
  import { Heading, Span, Mark, GradientButton, AccordionItem, Accordion, Input, Datepicker, Fileupload, Textarea, Label, Helper, Button, Select } from 'flowbite-svelte';
  import VerticalTabs from '../lib/components/VerticalTabs.svelte';
  import Stats from '../lib/components/Stats.svelte';
  import Buildsteps from '../lib/components/Buildsteps.svelte';
  import FilterLogoTech from '$lib/components/FilterLogoTech.svelte';
  import ProjectPortofolio from '$lib/components/ProjectPortofolio.svelte';
  import Typewriter from '$lib/components/Typewriter.svelte';
  import Saos from "saos";

  import { onMount, onDestroy } from 'svelte';

  let ServicesForm = [
    { value: "Web Custom Development", name: "Web Custom Development" },
    { value: "Mobile App Development", name: "Mobile App Development" },
    { value: "Data Visual With Dashboard", name: "Data Visual With Dashboard" },
    { value: "Landing Page Web / Company Profile", name: "Landing Page Web / Company Profile" },
    { value: "Digital Marketing, Advertising & SEO", name: "Digital Marketing, Advertising & SEO" },
    { value: "Design Branding & Content Creative", name: "Design Branding & Content Creative" },
  ];

   let KategoryCall = [
    { value: "Consultation", name: "Project Consultation" },
    { value: "Order", name: "Order Services" },
  ];

  let Budget = [
    { value: "< 1K USD", name: "< 1K USD" },
    { value: "1K - 3K USD", name: "1K - 3K USD" },
    { value: "3K - 5K USD", name: "3K - 5K USD" },
    { value: "5K - 10K USD", name: "5K - 10K USD" },
    { value: "10K USD", name: "> 10K USD" },
  ];

    // Variable untuk menyimpan kategori yang dipilih
  let selectedCategory = "";
  
  // Slide Testimony
  let containerTestimoni;
  let currentIndexTestimoni = 0;
  const reviews = [
    {
      name: "Indra Gunawan",
      date: "04 March 2025",
      rating: 5,
      text: "The website and mobile app created by this team truly exceeded expectations! The design is modern, the user experience is smooth, and the loading time is super fast. The development team was also very patient in explaining each feature and providing comprehensive training. Our sales increased 40% after launching the new website. Highly recommended for those who want to seriously upgrade their digital presence!"
    },
    {
      name: "Ayu Permatasari",
      date: "07 May 2025",
      rating: 5,
      text: "The digital marketing campaign was highly effective. ROI increased dramatically and brand awareness strengthened. The team was proactive in providing targeted insights and strategies."
    },
    {
      name: "Yoga Pranata",
      date: "19 Jun 2025",
      rating: 5,
      text: "Very professional service! The project was completed on time and met the brief. The mobile app is user-friendly and performs consistently. The support team is also responsive for maintenance."
    }
  ];
  
  function slideLeft() {
    if (currentIndexTestimoni > 0) {
      currentIndexTestimoni--;
    }
  }
  
  function slideRight() {
    if (currentIndexTestimoni < reviews.length - 1) {
      currentIndexTestimoni++;
    }
  }
  
  function handleTouchStart(e) {
    startX = e.touches[0].clientX;
  }
  
  function handleTouchEnd(e) {
    const endX = e.changedTouches[0].clientX;
    const diff = startX - endX;
    
    if (Math.abs(diff) > 50) {
      if (diff > 0) {
        slideRight();
      } else {
        slideLeft();
      }
    }
  }
  
  let startX = 0;

  // End Slide Testimony

   // Slide Carousel
  let currentSlide = 0;
  const slides = [
    {
      title: "Mobile App Development - Cross Platform",
      image: "/Images/Mobile App.webp",
      buttonText: "Learn More"
    },
    {
      title: "Web Development - With UI/UX",
      image: "/Images/Web Development.webp",
      buttonText: "Get Started"
    },
    {
      title: "Marketing Advertising",
      image: "/Images/Marketing Ads.webp",
      buttonText: "Enroll Now"
    }
  ];

  function nextSlide() {
    currentSlide = (currentSlide + 1) % slides.length;
  }

  function prevSlide() {
    currentSlide = (currentSlide - 1 + slides.length) % slides.length;
  }

  function goToSlide(index) {
    currentSlide = index;
  }

  // Auto-slide every 5 seconds
  let autoSlideInterval;
  
  function startAutoSlide() {
    autoSlideInterval = setInterval(nextSlide, 4000);
  }

  function stopAutoSlide() {
    clearInterval(autoSlideInterval);
  }
  onMount(() => {
    startAutoSlide();
  });

  onDestroy(() => {
    stopAutoSlide();
  });
</script>

<section style="background: linear-gradient(135deg, #e0f8ff 0%, #e9f6f8 50%, #b3d8d1 100%);margin-top:-32px;">
<div class="hero">
  <div class="grid grid-cols-1 md:grid-cols-3 lg:grid-cols-3 gap-2">
    <div class="col-span-2 rounded-xl pr-4">
      <Heading tag="h1" class="mb-4 text-4xl font-extrabold  md:text-5xl lg:text-5xl" style="line-height:1.2;">
        We are An Innovative <Mark class="dark:bg-blue-300 bg-blue-400">Digital Agency</Mark>. We Provide Services 
        <Span gradient="blueToGreen"><b><Typewriter /></b>
        </Span> 
      </Heading>
      
      <div class="mb-6" style="font-weight:600;">We Build a Strong Digital Foundation with Web and Mobile App Development, Increase your Visibility Through Digital Marketing, and Provide Valuable Business Insights with Dashboard Data Visualization.
      </div>
      <GradientButton pill color="greenToBlue">Let's get Started ➜</GradientButton> &nbsp;
      <GradientButton outline pill color="cyanToBlue">View our Portfolio ➜</GradientButton>
    </div> 

    <div class="rounded-xl">
     <center>
  <div 
    class="carousel-container" 
    on:mouseenter={stopAutoSlide} 
    on:mouseleave={startAutoSlide}
    role="region"
    aria-label="Image carousel"
  >
    <div class="carouselHeader">
      {#each slides as slide, index}
        <div class="slide" class:active={index === currentSlide}>
          <img src={slide.image} alt={slide.title} class="slide-image"/>
          <div class="slide-overlay"></div>
          <div class="slide-content">
            <h2>{slide.title}</h2>
            <button class="cta-button">
              {slide.buttonText}
            </button>
          </div>
        </div>
      {/each}

      <!-- Navigation Arrows 
      <button class="nav-arrow prev" on:click={prevSlide} aria-label="Previous slide">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M15 18l-6-6 6-6"/>
        </svg>
      </button>

      <button class="nav-arrow next" on:click={nextSlide} aria-label="Next slide">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M9 18l6-6-6-6"/>
        </svg>
      </button>
      -->
      <!-- Dot Indicators -->
      <div class="dots-container">
        {#each slides as _, index}
          <button 
            class="dot" 
            class:active={index === currentSlide}
            on:click={() => goToSlide(index)} 
            aria-label="Go to slide {index + 1}"
          ></button>
        {/each}
      </div>
    </div>
  </div>
</center>

    </div>
  </div>
</div>
</section>  
<br/><br/>

<section>
  <Stats />
</section>

  <!-- Section Apa yang dibangun. -->
<section id="Services">
   <div class="VerticalTabsBuild">
    <div class="relative flex justify-center items-center py-16 mb-2">
      <!-- Background circles -->
     <div class="absolute inset-0 flex justify-center items-center">
      <div class="w-32 h-32 bg-blue-100 rounded-full opacity-60 -translate-x-8 -translate-y-4"></div>
      <div class="w-24 h-24 bg-blue-200 rounded-full opacity-40 translate-x-12 translate-y-8"></div>
      <div class="w-16 h-16 bg-blue-300 rounded-full opacity-30 -translate-x-20 translate-y-12"></div>
     </div> 
     <!-- Main heading -->
     <Heading tag="h2" class="relative z-10 text-4xl font-extrabold text-center text-gray-800 max-w-2xl">
      What We Do
     </Heading>
   </div>
     <VerticalTabs />
  </div>
</section>
<br/>

<section>
    <Buildsteps />
</section>
<br/>


<section id="Contact">
     <div class="relative flex justify-center items-center py-16">
      <!-- Background circles -->
      <div class="absolute inset-0 flex justify-center items-center">
       <div class="w-32 h-32 bg-blue-100 rounded-full opacity-60 -translate-x-8 -translate-y-4"></div>
       <div class="w-24 h-24 bg-blue-200 rounded-full opacity-40 translate-x-12 translate-y-8"></div>
       <div class="w-16 h-16 bg-blue-300 rounded-full opacity-30 -translate-x-20 translate-y-12"></div>
     </div> 
      <!-- Main heading -->
      <Heading tag="h2" class="relative z-10 text-4xl font-extrabold text-center text-gray-800 max-w-2xl">
       Let's get started, Tell Us What You Will Create.
      </Heading>
   </div>

  <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-2 gap-2" style="padding: 4rem 1rem;max-width: 1200px;margin: 0 auto;">
    <div class="rounded-xl pr-4" style="margin-top:-80px;">
    <img src="/Images/Calling.webp" alt="Hanya menghubungi kami" style="transition: transform 0.3s ease;margin-left:220px;" />
      <div style="margin-top:-380px;text-shadow: 4px 2px 10px #090b17;">
        <h1 style="color:#edf4fb;font-weight:600;line-height: 1.2;">
          Please <Mark class="dark:bg-blue-300 bg-blue-400" style="background: #cbe3ff;">Tell Us</Mark> What You Would Like to Do in <Mark class="dark:bg-blue-300 bg-blue-400" style="background:#75dbec;">The Service Form</Mark> on The Side, We Will Respond to You According to Your Preferred Options.
        </h1></div>
    </div> 
    <Saos animation={'slide-in-fwd-tr 0.4s cubic-bezier(0.250, 0.460, 0.450, 0.940) both'}
animation_out={'scale-out-center 0.4s cubic-bezier(0.550, 0.085, 0.680, 0.530) both'}
top={250}
bottom={250}>
     <div class="rounded-xl" style="min-height:auto;height: fit-content;padding:20px;box-shadow:rgb(46 171 240 / 20%) -5px 5px, rgb(46 130 240 / 10%) 25px 25px, rgb(46 118 240 / 5%) 15px -20px, rgb(46 130 240 / 10%) 10px 13px, rgb(125 171 250 / 5%) -15px -35px;">
      <form>
      <div class="mb-4">
      <Label>Select Category</Label>
      <Select class="mt-2" items={KategoryCall}  bind:value={selectedCategory} />
      </div>
       <!-- Pilih Layanan - hanya tampil jika kategori = "Order Layanan" -->
      {#if selectedCategory === "Order"}
      <div class="mb-4">
      <Label>Select Service</Label>
      <Select class="mt-2" items={ServicesForm}  />
      </div>
       {/if}
       <div class="mb-4 grid gap-6 md:grid-cols-2">
      <div>
      <Label for="first_name" class="mb-1">Name</Label>
      <Input type="text" id="first_name" placeholder="John" required />
     </div>
      <div>
      <Label for="last_name" class="mb-1">Email Address</Label>
      <Input type="email" id="email" placeholder="john.doe@company.com" required />
      </div>
      </div>
      <div class="mb-4">
     <Label for="password" class="mb-2">Phone (Optional)</Label>
     <Input type="tel" id="phone" placeholder="123-45-678" pattern={"[0-9]{3}-[0-9]{2}-[0-9]{3}"} />
      </div>
       <!-- Budget - hanya tampil jika kategori = "Order Layanan" -->
         {#if selectedCategory === "Order"}
          <div class="mb-4">
         <Label> Budget </Label>
          <Select class="mt-2" items={Budget}  />
          </div>
          {/if}
         <div class="mb-2">
         <Label for="textarea-id" class="mb-2">Project Description</Label>
         <Textarea id="textarea-id" placeholder="Your message" rows={2} name="message" class="w-full" />
         </div>
       <!-- Deadline - hanya tampil jika kategori = "Order Layanan" -->
      {#if selectedCategory === "Order"}
      <div class="mb-4">
      <Label class="mb-1">Deadline</Label>
      <Datepicker locale="en-US" />
      </div>
      {/if}
      <div class="mb-6">
      <Label class="mb-2">File Attachment (Optional) [max. 20 MB]</Label>
      <Fileupload id="default_size" />
      </div>
       <GradientButton color="cyan" type="submit" class="w-full">Submit</GradientButton>
      </form>
      
     </div>
     </Saos>
   </div>
</section>
<br/>

<section>
     <div class="relative flex justify-center items-center py-16">
      <!-- Background circles -->
      <div class="absolute inset-0 flex justify-center items-center">
       <div class="w-32 h-32 bg-blue-100 rounded-full opacity-60 -translate-x-8 -translate-y-4"></div>
       <div class="w-24 h-24 bg-blue-200 rounded-full opacity-40 translate-x-12 translate-y-8"></div>
       <div class="w-16 h-16 bg-blue-300 rounded-full opacity-30 -translate-x-20 translate-y-12"></div>
     </div> 
      <!-- Main heading -->
      <Heading tag="h2" class="relative z-10 text-4xl font-extrabold text-center text-gray-800 max-w-2xl">
       We Work With The Latest Technology
      </Heading>
      </div>
      <center><FilterLogoTech /></center>
</section>
<br/>

<section id="Portofolio">
     <div class="relative flex justify-center items-center py-16">
      <!-- Background circles -->
      <div class="absolute inset-0 flex justify-center items-center">
       <div class="w-32 h-32 bg-blue-100 rounded-full opacity-60 -translate-x-8 -translate-y-4"></div>
       <div class="w-24 h-24 bg-blue-200 rounded-full opacity-40 translate-x-12 translate-y-8"></div>
       <div class="w-16 h-16 bg-blue-300 rounded-full opacity-30 -translate-x-20 translate-y-12"></div>
     </div> 
      <!-- Main heading -->
      <Heading tag="h2" class="relative z-10 text-4xl font-extrabold text-center text-gray-800 max-w-2xl">
       Our Portfolio
      </Heading>
   </div>
   <ProjectPortofolio />
</section>

<section class="hero grid grid-cols-1 md:grid-cols-3 lg:grid-cols-3 gap-2"> 
   <div class="rounded-xl pr-4">
     <div class="relative flex justify-center items-center py-16">
      <!-- Background circles -->
      <div class="absolute inset-0 flex justify-center items-center">
       <div class="w-32 h-32 bg-blue-100 rounded-full opacity-60 -translate-x-8 -translate-y-4"></div>
       <div class="w-24 h-24 bg-blue-200 rounded-full opacity-40 translate-x-12 translate-y-8"></div>
       <div class="w-16 h-16 bg-blue-300 rounded-full opacity-30 -translate-x-20 translate-y-12"></div>
     </div> 
      <!-- Main heading -->
       <Saos animation={'roll-in-blurred-left 0.65s cubic-bezier(0.230, 1.000, 0.320, 1.000) both'}
animation_out={'swirl-out-bck 0.6s ease-in both'}
top={150}
bottom={150}>
      <Heading tag="h2" class="relative z-10 text-4xl font-extrabold text-center text-gray-800 max-w-2xl">
       Testimonials What They Say
      </Heading>
      </Saos>
   </div>

   </div>
   <div class="col-span-2 rounded-xl">
     <div style="max-width: 800px;margin: 0 auto;padding: 20px;">
      <div class="carousel-wrapper" style="position: relative;display: flex;align-items: center; ">
      <button class="nav-btn left" on:click={slideLeft} disabled={currentIndexTestimoni === 0}> ← </button>
    
      <div class="carouselTestimoni" bind:this={containerTestimoni} style="flex: 1;overflow: hidden;border-radius: 12px;box-shadow:rgb(46 171 240 / 20%) -5px 5px, rgb(46 130 240 / 10%) 10px 10px, rgb(46 118 240 / 5%) 15px -15px;">
      <div class="carouselTestimoni-track" style="transform: translateX(-{currentIndexTestimoni * 100}%)"
         on:touchstart={handleTouchStart} on:touchend={handleTouchEnd} >
         {#each reviews as review, index}
          <div class="review-card" style="min-width: 100%;padding: 20px;background: white;border-radius: 12px;box-shadow: 0 2px 8px rgba(0,0,0,0.1);border: 1px solid #e5e7eb;">
             <div class="stars" style=" font-size: 16px;margin-bottom: 12px;">
              {#each Array(review.rating) as _}
                ⭐
              {/each}
             </div>
              <p class="review-text" style="font-size: 14px;line-height: 1.5;color: #374151;margin-bottom: 16px;font-style: italic;">"{review.text}"</p>
              <div class="author" style="display: flex;align-items: center;gap: 12px;">
               <div class="avatar" style="width: 40px;height: 40px;border-radius: 50%;background: #e9f2ff;display: flex;align-items: center;justify-content: center;font-weight: bold;color: #18a2be;">
                {review.name.charAt(0)}
               </div>
              <div class="author-info" style="flex: 1;">
                <div class="name" style="font-weight: 600;color: #111827;margin-bottom: 2px;">{review.name}</div>
                <div class="date" style="font-size: 12px;color: #6b7280;">{review.date}</div>
              </div>
            </div>
          </div>
        {/each}
      </div>
     </div>
     <button class="nav-btn right" on:click={slideRight} disabled={currentIndexTestimoni === reviews.length - 1}> → </button>
     </div>
  
      <div class="pagination">
       {#each reviews as _, index}
       <button class="pagination-dot {index === currentIndexTestimoni ? 'active' : ''}" on:click={() => currentIndexTestimoni = index}></button>
        {/each}
      </div>
       </div>
  </div>
</section>


<section class="faq"> 
<div class="py-10 px-8 md:px-26  lg:px-26"> 
  <div class="relative flex justify-center items-center py-16">
    <!-- Background circles -->
    <div class="absolute inset-0 flex justify-center items-center">
     <div class="w-32 h-32 bg-blue-100 rounded-full opacity-60 -translate-x-8 -translate-y-4"></div>
     <div class="w-24 h-24 bg-blue-200 rounded-full opacity-40 translate-x-12 translate-y-8"></div>
     <div class="w-16 h-16 bg-blue-300 rounded-full opacity-30 -translate-x-20 translate-y-12"></div>
   </div> 
   <!-- Main heading -->
   <Heading tag="h2" class="relative z-10 text-4xl font-extrabold text-center text-gray-800 max-w-2xl">
    Frequently Asked Questions (FAQ)
    </Heading>
   </div>
 <Accordion flush>
  <AccordionItem>
    {#snippet header()}<div class="flex items-center gap-2"><span class="text-base md:text-lg lg:text-xl">1. How long does it take to complete a website or mobile app project?</span></div>{/snippet}
    <p class="mb-2 text-gray-500 dark:text-gray-400">The development time varies depending on the complexity of the project. A simple company profile website typically takes 1-2 weeks, while an e-commerce or custom mobile app can take 1-3 months. We will provide a clear timeline after analyzing the requirements at the beginning of the project and provide regular progress updates.</p>
  </AccordionItem>
  <AccordionItem>
    {#snippet header()}<div class="flex items-center gap-2"><span class="text-base md:text-lg lg:text-xl">2. Are there maintenance and support services after the project is completed?</span></div>{/snippet}
    <p class="mb-2 text-gray-500 dark:text-gray-400">Yes, we provide ongoing maintenance and technical support. Maintenance packages include security updates, data backups, performance monitoring, and minor updates. For mobile apps, we also handle app store updates and bug fixes. Support is available through various channels with guaranteed response times.</p>
  </AccordionItem>
   <AccordionItem>
    {#snippet header()}<div class="flex items-center gap-2"><span class="text-base md:text-lg lg:text-xl">3. How do you measure the ROI of your digital marketing services?</span></div>{/snippet}
    <p class="mb-2 text-gray-500 dark:text-gray-400">We use various metrics and analytics tools to track ROI in real time. Each campaign is equipped with a visual data dashboard that displays key performance indicators such as conversion rate, cost per acquisition, website traffic, engagement rate, and revenue growth. Comprehensive reports are provided regularly with insights and optimization recommendations.</p>
  </AccordionItem>
   <AccordionItem>
    {#snippet header()}<div class="flex items-center gap-2"><span class="text-base md:text-lg lg:text-xl">4. Can I request custom features or designs specifically tailored to my business needs?</span></div>{/snippet}
    <p class="mb-2 text-gray-500 dark:text-gray-400">Of course! All of our solutions are custom and tailored to the unique needs of each client. Our team will conduct in-depth consultations to understand your business processes, target audience, and goals. From custom UI/UX design and specific functionalities to integration with existing systems, everything can be tailored to your requirements.</p>
  </AccordionItem>
</Accordion>
</div>
</section> 



<style>

 /**  Setting SAOS (Sveltekit Animation on Scroll) */

@keyframes -global-slide-in-fwd-tr {
  0% {
    transform: translateZ(-1400px) translateY(-800px) translateX(400px);
    opacity: 0;
  }
  100% {
    transform: translateZ(0) translateY(0) translateX(0);
    opacity: 1;
  }
}

@keyframes -global-scale-out-center {
  0% {
    transform: scale(1);
    opacity: 1;
  }
  100% {
    transform: scale(0);
    opacity: 0;
  }
}

@keyframes -global-roll-in-blurred-left {
  0% {
    transform: translateX(-1000px) rotate(-720deg);
    filter: blur(50px);
    opacity: 0;
  }
  100% {
    transform: translateX(0) rotate(0deg);
    filter: blur(0px);
    opacity: 1;
  }
}

/* Animasi Keluar - Swirl Out Back */
@keyframes -global-swirl-out-bck {
  0% {
    transform: rotate(0deg) scale(1);
    opacity: 1;
  }
  100% {
    transform: rotate(360deg) scale(0) translateZ(-2000px);
    opacity: 0;
  }
}

/** End Setting SAOS */

  .hero {
    padding: 4rem 1rem;
    max-width: 1200px;
    margin: 0 auto;
  }
  
  h1 {
    font-size: 3rem;
    margin-bottom: 1rem;
    color: #333;
  }
  
  p {
    font-size: 1.2rem;
    color: #666;
  }

/** CSS Carousel Header */
 .carousel-container {
    width: 100%;
    max-width: 1200px;
    margin: 0 auto;
    position: relative;
    border-radius: 20px;
    overflow: hidden;
  }

  .carouselHeader {
    position: relative;
    width: 100%;
    height: 380px;
    overflow: hidden;
  }

  .slide {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    padding: 0 60px;
    opacity: 0;
    transition: opacity 0.5s ease-in-out;
  }

  .slide.active {
    opacity: 1;
  }

  .slide-image {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-position: center;
    z-index: 1;
    animation: gentleFloat 4s ease-in-out infinite;
  }


@keyframes gentleFloat {
  0%, 100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-15px);
  }
}

  .slide-overlay {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 2;
  }

  .slide-content {
    position: relative;
    z-index: 3;
    color: white;
    max-width: 600px;
  }

  .slide-content h2 {
    font-size: 1rem;
    font-weight: 700;
    margin-bottom: 30px;
    line-height: 1.2;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
  }

  .cta-button {
    background: white;
    color: #333;
    border: none;
    margin-top: 140px;
    padding: 4px 18px;
    font-size: 1rem;
    font-weight: 600;
    border-radius: 25px;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
  }

  .cta-button:hover {
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
    background: #f8f9fa;
  }

  .nav-arrow {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background: rgba(255, 255, 255, 0.9);
    border: none;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.3s ease;
    z-index: 10;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
  }

  .nav-arrow:hover {
    background: white;
    transform: translateY(-50%) scale(1.1);
    box-shadow: 0 6px 20px rgba(0, 0, 0, 0.3);
  }

  .nav-arrow.prev {
    left: 20px;
    margin-top: 140px;
  }

  .nav-arrow.next {
    right: 20px;
    margin-top: 140px;
  }

  .nav-arrow svg {
    color: #333;
    width: 24px;
    height: 24px;
  }

  .dots-container {
    position: absolute;
    bottom: 30px;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    gap: 12px;
    z-index: 10;
  }

  .dot {
    width: 12px;
    height: 12px;
    border-radius: 50%;
    border: none;
    background: rgba(255, 255, 255, 0.5);
    cursor: pointer;
    transition: all 0.3s ease;
  }

  .dot.active {
    background: white;
    transform: scale(1.2);
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.3);
    width: 30px;
  }

  .dot:hover {
    background: rgba(255, 255, 255, 0.8);
  }

  /* Responsive Design */
  @media (max-width: 768px) {
    .slide {
      padding: 0 30px;
    }
    
    .slide-content h2 {
      font-size: 2rem;
    }
    
    .nav-arrow {
      width: 40px;
      height: 40px;
    }
    
    .nav-arrow.prev {
      left: 15px;
    }
    
    .nav-arrow.next {
      right: 15px;
    }
  }

  @media (max-width: 480px) {
    .slide-content h2 {
      font-size: 1.5rem;
    }
    
    .cta-button {
      padding: 12px 24px;
      font-size: 1rem;
    }
  }

   /***  CSS Vertical Tabs */

    .VerticalTabsBuild {
    max-width: 1400px;
    margin: 0 auto;
    padding: 40px 20px;
  }
  
 
  @media (max-width: 768px) {
    .VerticalTabsBuild {
      padding: 20px 10px;
    }  
  }

  /***  CSS Carousel Testimony */

  .carousel-wrapper {
		gap: 10px;
  }
  
  .carouselTestimoni-track {
    display: flex;transition: transform 0.3s ease;
  }
  
  .nav-btn {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    border: 1px solid #d1d5db;
    background: white;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: all 0.2s;
    font-size: 18px;
    color: #374151;
  }
  
  .nav-btn:hover:not(:disabled) {
    background: #f3f4f6;
    border-color: #9ca3af;
  }
  
  .nav-btn:disabled {
    opacity: 0.5;
    cursor: not-allowed;
  }
  
  .pagination {
    display: flex;
    justify-content: center;
    gap: 8px;
    margin-top: 16px;
  }
  
  .pagination-dot {
    width: 8px;
    height: 8px;
    border-radius: 50%;
    border: none;
    background: #d1d5db;
    cursor: pointer;
    transition: background 0.2s;
  }
  
  .pagination-dot.active {
    background: #3b82f6;
  }
  
  .pagination-dot:hover {
    background: #9ca3af;
  }
  
  .pagination-dot.active:hover {
    background: #2563eb;
  }
  
  /* Responsive */
  @media (max-width: 640px) {
    .carousel-wrapper {
      gap: 5px;
    }
    
    .nav-btn {
      width: 35px;
      height: 35px;
      font-size: 16px;
    }
    
    .review-card {
      padding: 16px;
    }
  }


 
</style>