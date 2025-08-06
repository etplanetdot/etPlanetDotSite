<script>
  import Saos from "saos";
  
  // Data logo berdasarkan kategori
  const logos = [
    {
      name: "SvelteKit",
      image: "/Images/logos/Sveltekit.png",
      category: "Web Development"
    },
    {
      name: "Nuxt Js",
      image: "/Images/logos/Nuxt Js.png",
      category: "Web Development"
    },
    {
      name: "WordPress",
      image: "/Images/logos/Wordpress.png",
      category: "Web Development"
    },
    {
      name: "Next.js",
      image: "/Images/logos/nextjs.png",
      category: "Web Development"
    },
    {
      name: "Just in Mind",
      image: "/Images/logos/JustinMind.png",
      category: "Design UI/UX"
    },
    {
      name: "Figma",
      image: "/Images/logos/Figma.png",
      category: "Design UI/UX"
    },
    {
      name: "Tailwind CSS",
      image: "/Images/logos/Tailwind Css.png",
      category: "Design UI/UX"
    },
    {
      name: "Flutter",
      image: "/Images/logos/Flutter.png",
      category: "Mobile App"
    },
    {
      name: "Supabase",
      image: "/Images/logos/Supabase.png",
      category: "Database"
    },
    {
      name: "Appwrite",
      image: "/Images/logos/Appwrite.png",
      category: "Database"
    },
    {
      name: "PostgreSQL",
      image: "/Images/logos/PostgreSQL.png",
      category: "Database"
    },
    {
      name: "Google Ads",
      image: "/Images/logos/Google Ads.png",
      category: "Marketing"
    }
  ];

  // Kategori yang tersedia
  const categories = ["All", "Web Development", "Design UI/UX", "Mobile App", "Database", "Marketing"];
  
  // State untuk kategori yang aktif
  let activeCategory = "All";
  
  // Reactive statement untuk filter logo
  $: filteredLogos = activeCategory === "All" 
    ? logos 
    : logos.filter(logo => logo.category === activeCategory);

  // Function untuk handle click kategori
  function handleCategoryClick(category) {
    console.log('Category clicked:', category);
    activeCategory = category;
  }
</script>

<div class="container">
  <!-- Tab Navigation -->
  <div class="tab-container">
    {#each categories as category}
      <button 
        class="tab-button {activeCategory === category ? 'active' : ''}"
        on:click={() => handleCategoryClick(category)}
        type="button"
      >
        {category}
      </button>
    {/each}
  </div>

  <!-- Logo Grid dengan animasi per item -->
  <div class="logo-grid-wrapper">
    <div class="logo-grid">
      {#each filteredLogos as logo, index (logo.name)}
        <Saos 
          animation={'from-left 0.7s cubic-bezier(0.35, 0.5, 0.65, 0.95) both'} 
          animation_out={'flip-out-hor-top 0.45s cubic-bezier(0.550, 0.085, 0.680, 0.530) both'}
          top={100}
          bottom={150}
          delay={index * 50}
        >
          <div class="logo-item">
            <img src={logo.image} alt={logo.name} loading="lazy" />
            <span class="logo-name">{logo.name}</span>
          </div>
        </Saos>
      {/each}
    </div>
  </div>
</div>

<style>
  /* Setting SAOS (Sveltekit Animation on Scroll) */
  @keyframes -global-from-left {
    0% {
      transform: rotateX(50deg) translateX(-200vw) skewX(-50deg);
      opacity: 0;
    }
    100% {
      transform: rotateX(0deg) translateX(0) skewX(0deg);
      opacity: 1;
    }
  }

  @keyframes -global-flip-out-hor-top {
    0% {
      transform: rotateX(0);
      opacity: 1;
    }
    100% {
      transform: rotateX(-90deg);
      opacity: 0;
    }
  }
  /* End Setting SAOS */

  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 20px;
  }

  .tab-container {
    display: flex;
    gap: 10px;
    margin-bottom: 30px;
    flex-wrap: wrap;
    justify-content: center;
    position: relative;
    z-index: 20;
  }

  .tab-button {
    padding: 12px 24px;
    background-color: #f5f5f5;
    border: 2px solid #ddd;
    border-radius: 25px;
    cursor: pointer;
    font-size: 14px;
    font-weight: 500;
    transition: all 0.3s ease;
    color: #666;
    outline: none;
    position: relative;
    z-index: 101;
    pointer-events: auto;
  }

  .tab-button:hover {
    background-color: #e2f5f8;
    border-color: #90bac6;
    transform: translateY(-2px);
  }

  .tab-button:active {
    transform: translateY(0);
  }

  .tab-button.active {
    background-color: #84dded;
    border-color: #8dabb4;
    color: white;
  }

  /* Wrapper untuk logo grid dengan tinggi tetap */
  .logo-grid-wrapper {
    min-height: 300px; /* Tinggi minimum yang konsisten */
    position: relative;
  }

  .logo-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 2fr));
    gap: 20px;
    align-items: center;
    /* Hapus min-height dari sini karena sudah ada di wrapper */
  }

  .logo-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    padding: 4px 2px;
    transition: transform 0.2s ease;
    border-radius: 10px;
    background-color: transparent;
  }

  .logo-item:hover {
    transform: translateY(-5px);
    background-color: rgba(0, 0, 0, 0.02);
  }

  .logo-item img {
    width: 50px;
    height: 50px;
    object-fit: contain;
    margin-bottom: 15px;
    transition: transform 0.2s ease;
  }

  .logo-item:hover img {
    transform: scale(1.1);
  }

  .logo-name {
    font-size: 16px;
    font-weight: 500;
    color: #333;
    line-height: 1.2;
  }

  /* Responsive Design */
  @media (max-width: 768px) {
    .container {
      padding: 15px;
    }
    
    .tab-container {
      justify-content: center;
      gap: 8px;
    }
    
    .tab-button {
      padding: 10px 18px;
      font-size: 13px;
    }
    
    .logo-grid-wrapper {
      min-height: 250px; /* Sesuaikan untuk mobile */
    }
    
    .logo-grid {
      grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
      gap: 15px;
    }
    
    .logo-item {
      padding: 15px 8px;
    }
    
    .logo-item img {
      width: 40px;
      height: 40px;
    }
    
    .logo-name {
      font-size: 14px;
    }
  }

  @media (max-width: 480px) {
    .tab-button {
      padding: 8px 16px;
      font-size: 12px;
    }
    
    .logo-grid-wrapper {
      min-height: 200px; /* Sesuaikan untuk mobile kecil */
    }
    
    .logo-grid {
      grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
      gap: 12px;
    }
    
    .logo-item img {
      width: 35px;
      height: 35px;
    }
    
    .logo-name {
      font-size: 13px;
    }
  }

  /* Loading state */
  .logo-item img[src=""] {
    background-color: #f0f0f0;
    animation: pulse 1.5s ease-in-out infinite;
  }

  @keyframes pulse {
    0%, 100% {
      opacity: 1;
    }
    50% {
      opacity: 0.5;
    }
  }
</style>