<script lang="ts">
  import { page } from '$app/stores';
  import { goto } from '$app/navigation';
  import '../app.css';
  import { Footer, FooterCopyright, FooterLinkGroup, FooterLink, FooterBrand, FooterIcon, SpeedDial, SpeedDialTrigger, SpeedDialButton  } from "flowbite-svelte";
  import { FacebookSolid, GithubSolid, DiscordSolid, TwitterSolid, WhatsappSolid, EnvelopeSolid, FileCopySolid, UserHeadsetOutline } from "flowbite-svelte-icons";

  let { children } = $props();
  
  let mobileMenuOpen = $state(false);
  
  const navigation = [
    { name: 'Home', href: '/' },
    { name: 'About Us', href: '/about' },
    { name: 'Services', href: '/#Services' },
    { name: 'Packages', href: '/packages' },
    { name: 'Portofolio', href: '/#Portofolio' },
    { name: 'Contact', href: '/#Contact' },
    { name: 'Login', href: '/login' }
  ];
  
  function toggleMobileMenu() {
    mobileMenuOpen = !mobileMenuOpen;
  }
  
  function handleNavigation(href: string) {
    goto(href);
    mobileMenuOpen = false;
  }

</script>

<svelte:head>
  <title>Your Website</title>
  <meta name="description" content="Your website description" />
</svelte:head>

<!-- Header -->
<header class="header">
  <div class="container">
    <div class="logo">
      <a href="/" class="logo-link" style="display:flex;">
       <img src="Images/PlanetDot.png" alt="planetdot" style="height:40px;width:40px;" /> <h1>@PlanetDot</h1>
      </a>
    </div>
    
    <nav class="desktop-nav">
      {#each navigation as item}
        <a
          href={item.href}
          class="nav-link {item.name === 'Login' ? 'nav-login-btn' : ''}"
          class:active={$page.url.pathname === item.href}
        >
          {item.name}
        </a>
      {/each}
    </nav>
    
    <button class="mobile-menu-btn" onclick={toggleMobileMenu}>
      {#if mobileMenuOpen}
        <span class="close-icon">✕</span>
      {:else}
        <span class="hamburger"></span>
        <span class="hamburger"></span>
        <span class="hamburger"></span>
      {/if}
    </button>
  </div>
  
   {#if mobileMenuOpen}
    <nav class="mobile-nav">
      {#each navigation as item}
        <button
          class="mobile-nav-link {item.name === 'Login' ? 'mobile-nav-login-btn' : ''}"
          class:active={$page.url.pathname === item.href}
          onclick={() => handleNavigation(item.href)}
        >
          {item.name}
        </button>
      {/each}
    </nav>
  {/if}
</header>

<!-- Main Content -->
<main>
  {@render children()}
</main>

<SpeedDialTrigger class="fixed end-6 bottom-6" color="cyan" shadow gradient >
{#snippet icon()}
    <UserHeadsetOutline class="h-10 w-10" />
  {/snippet}
</SpeedDialTrigger>
<SpeedDial>
  <SpeedDialButton name="Whatsapp">
    <WhatsappSolid class="h-8 w-8" />
  </SpeedDialButton>
 <SpeedDialButton name="Email">
    <EnvelopeSolid class="h-8 w-8" />
  </SpeedDialButton>
</SpeedDial>

<Footer footerType="socialmedia" style="background-image:url(/Images/FooterBackground.png);background-size: 100% 120%;background-repeat: no-repeat;padding: 1rem 6rem;aspect-ratio: 18/3;">
  <div class="md:flex md:justify-between">
    <div class="mb-6 md:mb-0">
      <FooterBrand href="#" src="Images/PlanetDot.png" alt="PlanetDot Logo" name="@PlanetDot" />
     <br/><div>Planet Dot is a creative digital agency, your strategic partner in developing <br/>products and businesses in the digital age. We provide innovative solutions<br/>to transform ideas into profitable digital realities. <br/>
	   <br/><h2 style="font-weight:600;">Address</h2>
	   Jakarta - Indonesia<br/>
	   Email: info@agency.com
	 </div> 
	</div>

    <div class="grid grid-cols-2 gap-8 sm:grid-cols-2 sm:gap-6">
      <div>
        <h2 class="mb-6 text-sm font-semibold text-gray-900 uppercase dark:text-white">Resources</h2>
        <FooterLinkGroup>
          <FooterLink class="mb-4" href="/">Flowbite</FooterLink>
          <FooterLink class="mb-4" href="/">Tailwind CSS</FooterLink>
        </FooterLinkGroup>
      </div>
      
      <div>
        <h2 class="mb-6 text-sm font-semibold text-gray-900 uppercase dark:text-white">Legal</h2>
        <FooterLinkGroup>
          <FooterLink class="mb-4" href="/">Privacy Policy</FooterLink>
          <FooterLink class="mb-4" href="/">Terms & Conditions</FooterLink>
        </FooterLinkGroup>
      </div>
    </div>
  </div>
  <hr class="my-6 border-gray-200 sm:mx-auto lg:my-8 dark:border-gray-700" />
  <div class="sm:flex sm:items-center sm:justify-between">
    <FooterCopyright href="/" by="Flowbite™" />
    <div class="mt-4 flex space-x-6 sm:mt-0 sm:justify-center rtl:space-x-reverse">
      <FooterIcon href="/">
        <FacebookSolid class="h-5 w-5 text-gray-500 hover:text-gray-900 dark:text-gray-500 dark:hover:text-white" />
      </FooterIcon>
      <FooterIcon href="/">
        <DiscordSolid class="h-5 w-5 text-gray-500 hover:text-gray-900 dark:text-gray-500 dark:hover:text-white" />
      </FooterIcon>
      <FooterIcon href="/">
        <TwitterSolid class="h-5 w-5 text-gray-500 hover:text-gray-900 dark:text-gray-500 dark:hover:text-white" />
      </FooterIcon>
      <FooterIcon href="/">
        <GithubSolid class="h-5 w-5 text-gray-500 hover:text-gray-900 dark:text-gray-500 dark:hover:text-white" />
      </FooterIcon>
    </div>
  </div>
</Footer>

<!-- Footer (optional) 
<footer class="footer">
  <div class="container">
    <p>&copy; 2025 Your Website. All rights reserved.</p>
  </div>
</footer>
-->

<style>
  :global(body) {
    margin: 0;
    padding: 0;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  }
  
  .header {
    background: white;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    position: sticky;
    top: 0;
    z-index: 100;
  }
  
  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 1rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 4rem;
  }
  
  .logo-link {
    text-decoration: none;
    color: #333;
  }
  
  .logo h1 {
    margin: 0;
    font-size: 1.5rem;
    font-weight: 700;
    color: #007acc;
  }
  
  .desktop-nav {
    display: flex;
    gap: 2rem;
  }
  
  .nav-link {
    text-decoration: none;
    color: #666;
    font-weight: 500;
    transition: color 0.2s;
    position: relative;
  }
  
  .nav-link:hover,
  .nav-link.active {
    color: #007acc;
  }
  
  .nav-link.active::after {
    content: '';
    position: absolute;
    bottom: -8px;
    left: 0;
    right: 0;
    height: 2px;
    background: #007acc;
  }
  
  .mobile-menu-btn {
    display: none;
    background: none;
    border: none;
    flex-direction: column;
    gap: 3px;
    cursor: pointer;
    padding: 0.5rem;
    align-items: center;
    justify-content: center;
    width: 40px;
    height: 40px;
  }
  
  .hamburger {
    width: 20px;
    height: 2px;
    background: #333;
    transition: 0.3s;
  }
  
  .close-icon {
    font-size: 20px;
    color: #333;
    font-weight: 300;
    line-height: 1;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
  .mobile-nav {
    display: none;
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    background: white;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    flex-direction: column;
    padding: 1rem;
  }
  
  .mobile-nav-link {
    background: none;
    border: none;
    text-align: left;
    padding: 0.75rem 0;
    color: #666;
    font-weight: 500;
    cursor: pointer;
    transition: color 0.2s;
    border-bottom: 1px solid #eee;
  }
  
  .mobile-nav-link:last-child {
    border-bottom: none;
  }
  
  .mobile-nav-link:hover,
  .mobile-nav-link.active {
    color: #007acc;
  }
  
  main {
    min-height: calc(100vh - 8rem);
    padding: 2rem 0;
  }
  
  .footer {
    background: #f8f9fa;
    border-top: 1px solid #eee;
    padding: 2rem 0;
    text-align: center;
  }
  
  .footer p {
    margin: 0;
    color: #666;
  }

  /* Gaya untuk tombol Contact di desktop */
.nav-login-btn {
  background-color: #007acc; /* Warna latar belakang biru */
  color: white !important; /* Warna teks putih */
  padding: 0.4rem 1rem; /* Padding internal */
  border-radius: 12px; /* Sudut membulat */
  transition: background-color 0.2s, transform 0.2s; /* Transisi halus */
  font-weight: 600; /* Tebal sedikit */
  margin-left: 1rem; /* Sedikit jarak dari item nav lainnya */
  box-shadow: 0 2px 5px rgba(0, 122, 204, 0.3); /* Efek bayangan */
  text-decoration: none; /* Pastikan tidak ada garis bawah */
}

.nav-login-btn:hover {
  background-color: #005f99; /* Warna latar belakang lebih gelap saat hover */
 
}

/* Hapus indikator 'active' di bawah untuk tombol Contact */
.nav-login-btn.active::after {
  content: none;
}

/* Gaya untuk tombol Login di mobile (dalam menu hamburger) */
.mobile-nav-login-btn {
  background-color: #007acc; /* Warna latar belakang biru */
  color: white; /* Warna teks putih */
  padding: 0.75rem 1rem; /* Padding internal */
  border-radius: 5px; /* Sudut membulat */
  margin-top: 0.5rem; /* Jarak dari item mobile nav sebelumnya */
  width: 100%; /* Lebar penuh */
  text-align: center;/* Teks di tengah */
  font-weight: 600; /* Tebal sedikit */
  box-shadow: 0 2px 5px rgba(0, 122, 204, 0.3); /* Efek bayangan */
  transition: background-color 0.2s;
}

.mobile-nav-login-btn:hover {
  background-color: #005f99; /* Warna latar belakang lebih gelap saat hover */
 color: white; 
}

/* Hapus border-bottom untuk tombol login di mobile */
.mobile-nav-login-btn:last-child {
  border-bottom: none;
}

/* Sesuaikan gaya untuk tautan mobile aktif jika diperlukan, mungkin tidak ingin border bawah pada tombol */
.mobile-nav-link.active {
  font-weight: 700; /* Contoh: membuat teks lebih tebal */
  color: #007acc;
}
  
  @media (max-width: 768px) {
    .desktop-nav {
      display: none;
    }
    
    .mobile-menu-btn {
      display: flex;
    }
    
    .mobile-nav {
      display: flex;
    }
  }
</style>