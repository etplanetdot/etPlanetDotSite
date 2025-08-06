<script>
  import Saos from "saos";
  // Data portfolio projects
  let projects = [
    {
      id: 1,
      title: "E-Commerce Website",
      description: "Full-stack e-commerce platform with payment integration and admin dashboard. Built with modern technologies.",
      image: "https://picsum.photos/1200/600?random=1",
      link: "#"
    },
    {
      id: 2,
      title: "Task Management App",
      description: "Collaborative task management application with real-time updates and team collaboration features.",
      image: "https://picsum.photos/1200/600?random=2",
      link: "#"
    },
    {
      id: 3,
      title: "Weather Dashboard",
      description: "Interactive weather dashboard with location-based forecasts and beautiful data visualizations.",
      image: "https://picsum.photos/1200/600?random=3",
      link: "#"
    },
    {
      id: 4,
      title: "Social Media Platform",
      description: "Modern social media platform with user authentication, posts, and real-time messaging system.",
      image: "https://picsum.photos/1200/600?random=4",
      link: "#"
    },
    {
      id: 5,
      title: "Portfolio Website",
      description: "Responsive portfolio website with smooth animations and modern design principles.",
      image: "https://picsum.photos/1200/600?random=5",
      link: "#"
    }
  ];

  let currentIndex = 0;
  let itemsPerView = 3;
  let carouselContainer;

  // Responsive items per view
  $: {
    if (typeof window !== 'undefined') {
      if (window.innerWidth < 768) {
        itemsPerView = 1;
      } else if (window.innerWidth < 1024) {
        itemsPerView = 2;
      } else {
        itemsPerView = 3;
      }
    }
  }

  // Calculate maximum index
  $: maxIndex = Math.max(0, projects.length - itemsPerView);

  // Navigation functions with infinite loop
  function nextSlide() {
    if (currentIndex < maxIndex) {
      currentIndex++;
    } else {
      // Kembali ke slide pertama ketika mencapai akhir
      currentIndex = 0;
    }
  }

  function prevSlide() {
    if (currentIndex > 0) {
      currentIndex--;
    } else {
      // Pergi ke slide terakhir ketika di slide pertama
      currentIndex = maxIndex;
    }
  }

  // Keyboard navigation
  function handleKeydown(event) {
    if (event.key === 'ArrowLeft') {
      prevSlide();
    } else if (event.key === 'ArrowRight') {
      nextSlide();
    }
  }

  // Auto-slide functionality (optional)
  let autoSlide = false;
  let intervalId;

  function startAutoSlide() {
    if (autoSlide) {
      intervalId = setInterval(nextSlide, 5000);
    }
  }

  function stopAutoSlide() {
    if (intervalId) {
      clearInterval(intervalId);
    }
  }

  $: if (autoSlide) {
    startAutoSlide();
  } else {
    stopAutoSlide();
  }

  // Function untuk navigasi langsung ke slide tertentu
  function goToSlide(index) {
    currentIndex = index;
  }
</script>

<svelte:window on:keydown={handleKeydown} />

<div class="portfolio-carousel">
  <div class="carousel-header">
    
    <div class="carousel-controls">
      <button 
        class="nav-btn prev-btn" 
        on:click={prevSlide}
        aria-label="Previous projects"
      >
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor">
          <path d="M15 18l-6-6 6-6"/>
        </svg>
      </button>
      
      <button 
        class="nav-btn next-btn" 
        on:click={nextSlide}
        aria-label="Next projects"
      >
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor">
          <path d="M9 18l6-6-6-6"/>
        </svg>
      </button>
    </div>
  </div>
<Saos animation={'swing-in-top-fwd 0.5s cubic-bezier(0.175, 0.885, 0.320, 1.275) both'}>
  <div class="carousel-container" bind:this={carouselContainer} on:mouseenter={stopAutoSlide}
    on:mouseleave={() => autoSlide && startAutoSlide()}>
    <div class="carousel-track" style="transform: translateX(-{currentIndex * (100 / itemsPerView)}%)">
      {#each projects as project, index}
        <div class="project-card">
          <div class="project-image">
            <img src={project.image} alt={project.title} />
            <div class="image-overlay">
              <span>View Details</span>
            </div>
          </div>
          
          <div class="project-content">
            <h3 class="project-title">{project.title}</h3>
            <p class="project-description">{project.description}</p>
            <a href={project.link} class="view-project-btn">
              View Project
            </a>
          </div>
        </div>
      {/each}
    </div>

  </div>
  </Saos>

  <!-- Indicators -->
  <div class="carousel-indicators">
    {#each Array(maxIndex + 1) as _, index}
      <button 
        class="indicator {index === currentIndex ? 'active' : ''}"
        on:click={() => goToSlide(index)}
        aria-label="Go to slide {index + 1}"
      ></button>
    {/each}
  </div>

  <!-- Navigation info (optional) 
  <div class="carousel-info">
    <span class="slide-counter">
      {currentIndex + 1} / {maxIndex + 1}
    </span>
  </div>
  -->
</div>


<style>


/**  Setting SAOS (Sveltekit Animation on Scroll) */

/* Animasi Masuk - Swing In Top Forward */
@keyframes -global-swing-in-top-fwd {
  0% {
    transform: rotateX(-100deg) translateZ(400px) translateY(-300px);
    transform-origin: top;
    opacity: 0;
  }
  100% {
    transform: rotateX(0deg) translateZ(0) translateY(0);
    transform-origin: top;
    opacity: 1;
  }
}


/** End Setting SAOS */

  .portfolio-carousel {
    max-width: 1200px;
    margin: 0 auto;
    padding: 2rem 1rem;
  }

  .carousel-header {
    justify-content: space-between;
    align-items: center;
    margin-bottom: 2rem;
  }

  .carousel-header h2 {
    font-size: 2.5rem;
    font-weight: 700;
    color: #2d3748;
    margin: 0;
  }

  .carousel-controls {
    display: flex;
    gap: 0.5rem;
    justify-content: end;
  }

  .nav-btn {
    width: 48px;
    height: 48px;
    border-radius: 50%;
    border: 2px solid #5C82FF;
    background: white;
    color: #4a5568;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.3s ease;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  }

  .nav-btn:hover {
    background: #7092FF;
    color: white;
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  }

  .nav-btn:active {
    transform: translateY(0);
  }

  .carousel-container {
    overflow: hidden;
    border-radius: 1rem;
  }

  .carousel-track {
    display: flex;
    transition: transform 0.5s cubic-bezier(0.4, 0, 0.2, 1);
    gap: 1.5rem;
  }

  .project-card {
    flex: 0 0 calc(33.333% - 1rem);
    background: white;
    border-radius: 1rem;
    overflow: hidden;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
    transition: all 0.3s ease;
    border: 1px solid #e2e8f0;
  }

  .project-card:hover {
    transform: translateY(-8px);
    box-shadow: 0 8px 30px rgba(0, 0, 0, 0.15);
  }

  .project-image {
    position: relative;
    height: 200px;
    background: #e5f1ff;
    overflow: hidden;
  }

  .project-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.3s ease;
  }

  .project-card:hover .project-image img {
    transform: scale(1.05);
  }

  .image-overlay {
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(229, 241, 255, 0.8);
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0.5;
    transition: opacity 0.3s ease;
    color: white;
    font-weight: 600;
  }

  .project-card:hover .image-overlay {
    opacity: 0;
  }

  .project-content {
    padding: 1.5rem;
  }

  .project-title {
    font-size: 1.25rem;
    font-weight: 600;
    color: #2d3748;
    margin: 0 0 0.75rem 0;
    line-height: 1.3;
  }

  .project-description {
    color: #4a5568;
    font-size: 0.9rem;
    line-height: 1.5;
    margin: 0 0 1.5rem 0;
  }

  .view-project-btn {
    display: inline-block;
    background: #7092FF;
    color: white;
    text-decoration: none;
    padding: 0.75rem 1.5rem;
    border-radius: 0.5rem;
    font-weight: 500;
    transition: all 0.3s ease;
    text-align: center;
    width: 100%;
    box-sizing: border-box;
  }

  .view-project-btn:hover {
    background: #5C82FF;
    transform: translateY(-1px);
  }

  .carousel-indicators {
    display: flex;
    justify-content: center;
    gap: 0.5rem;
    margin-top: 2rem;
  }

  .indicator {
    width: 12px;
    height: 12px;
    border-radius: 50%;
    border: none;
    background: #cbd5e0;
    cursor: pointer;
    transition: all 0.3s ease;
  }

  .indicator.active {
    background: #cbe3ff;
    transform: scale(1.2);
  }

  .indicator:hover {
    background: #cbe3ff;
  }

  .carousel-info {
    display: flex;
    justify-content: center;
    margin-top: 1rem;
  }

  .slide-counter {
    color: #718096;
    font-size: 0.9rem;
    font-weight: 500;
  }

  /* Responsive Design */
  @media (max-width: 1024px) {
    .project-card {
      flex: 0 0 calc(50% - 0.75rem);
    }
    
    .carousel-header h2 {
      font-size: 2rem;
    }
  }

  @media (max-width: 768px) {
    .project-card {
      flex: 0 0 100%;
    }
    
    .carousel-header {
      flex-direction: column;
      gap: 1rem;
      text-align: center;
    }
    
    .carousel-header h2 {
      font-size: 1.75rem;
    }
    
    .portfolio-carousel {
      padding: 1rem 0.5rem;
    }
    
    .carousel-track {
      gap: 1rem;
    }
  }

  @media (max-width: 480px) {
    .nav-btn {
      width: 40px;
      height: 40px;
    }
    
    .project-content {
      padding: 1rem;
    }
    
    .project-image {
      height: 160px;
    }
  }
</style>