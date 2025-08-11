<!-- VerticalTabs.svelte -->
<script>
  import { Badge } from "flowbite-svelte";
  import { BookmarkSolid } from "flowbite-svelte-icons";
  import { onMount } from 'svelte';
  import Saos from "saos";

  function openWhatsAppWebDevelopment() {
    const phoneNumber = "6282193168305";
    const message = "Halo, saya ingin bertanya tentang pembuatan Web App Development...";
    const url = `https://wa.me/${phoneNumber}?text=${encodeURIComponent(message)}`;
    window.open(url, '_blank');
  }

  function openWhatsAppMobileAppDevelopment() {
    const phoneNumber = "6282193168305";
    const message = "Halo, saya ingin bertanya tentang pembuatan Mobile App Development...";
    const url = `https://wa.me/${phoneNumber}?text=${encodeURIComponent(message)}`;
    window.open(url, '_blank');
  }

  function openWhatsAppDataVisualDashboard() {
    const phoneNumber = "6282193168305";
    const message = "Halo, saya ingin bertanya tentang pembuatan Data Visual Dashboard...";
    const url = `https://wa.me/${phoneNumber}?text=${encodeURIComponent(message)}`;
    window.open(url, '_blank');
  }

  function openWhatsAppLandingPage() {
    const phoneNumber = "6282193168305";
    const message = "Halo, saya ingin bertanya tentang pembuatan Web Design & Landing Page...";
    const url = `https://wa.me/${phoneNumber}?text=${encodeURIComponent(message)}`;
    window.open(url, '_blank');
  }

  function openWhatsAppDigitalMarketing() {
    const phoneNumber = "6282193168305";
    const message = "Halo, saya ingin bertanya tentang Digital Marketing, SEO & Advertising...";
    const url = `https://wa.me/${phoneNumber}?text=${encodeURIComponent(message)}`;
    window.open(url, '_blank');
  }

  function openWhatsAppDesignBranding() {
    const phoneNumber = "6282193168305";
    const message = "Halo, saya ingin bertanya tentang Design Branding & Content...";
    const url = `https://wa.me/${phoneNumber}?text=${encodeURIComponent(message)}`;
    window.open(url, '_blank');
  }
  
  // Data tabs dengan icon dan konten
  const tabs = [
    {
      id: 'website',
      title: 'Web App Development (Custom)',
      icon: '⬡',
      price: 'Start From 5jt IDR - 50jt IDR',
      content: `
       <center><img src="/Images/Web Development Service.webp" style="width:80%;height:350px;margin-bottom:10px;transition: transform 0.3s ease;" /></center>
        <p style="color:#0b6a7e;font-weight:500;">We transform your digital ideas into robust, solution-oriented web applications. Our team of experts builds tailored solutions for your unique business needs, from portals and dashboards to complex system integrations for more efficient data management.</p>
        <div class="grid grid-cols-2 gap-4">
          <div>
          <ul>
          <li>✅ Web Applications & Custumization</li>
          <li>✅ Ecommerce Development</li>
          </ul>
          </div>
           <div>
            <ul>
            <li>✅ API Integrations & database</li>
            <li>✅ Portal & Dashboard Development</li>
            </ul>
          </div>
        </div> <br/>
        <center><button class="whatsapp-btn" data-service="website">
        <svg class="whatsapp-icon" viewBox="0 0 24 24" fill="currentColor">
        <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.890-5.335 11.893-11.893A11.821 11.821 0 0020.886 3.488"/>
        </svg> CALL US</button>
        </center>
      `
    },
    {
      id: 'mobile',
      title: 'Mobile App Development',
      icon: '⬡',
      price: 'Start From 20jt IDR - 100jt IDR',
      content: `
       <center><img src="/Images/Mobile App Development Service.webp" style="width:80%;height:350px;margin-bottom:10px;transition: transform 0.3s ease;" /></center>
       <p style="color:#0b6a7e;font-weight:500;">Turn your brilliant idea into a powerful and intuitive mobile app. We specialize in creating native (iOS & Android) and cross-platform apps that deliver exceptional user experiences to reach your audience everywhere.</p>
        <div class="grid grid-cols-2 gap-4">
          <div>
          <ul>
          <li>✅ Native iOS & Android Apps</li>
          <li>✅ Cross-platform Development</li>
          </ul>
          </div>
           <div>
            <ul>
            <li>✅ UI/UX Mobile Design</li>
            <li>✅ App Store Optimization</li>
            </ul>
          </div>
        </div><br/>
        <center><button class="whatsapp-btn" data-service="mobile">
        <svg class="whatsapp-icon" viewBox="0 0 24 24" fill="currentColor">
        <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.890-5.335 11.893-11.893A11.821 11.821 0 0020.886 3.488"/>
        </svg> CALL US</button>
        </center>
      `
    },
    {
      id: 'datavisual',
      title: 'Data Visual Dashboard',
      icon: '⬡',
      price: 'Start From 20jt IDR - 100jt IDR',
      content: `
      <center><img src="/Images/Dashboard Visual Data.webp" style="width:80%;height:350px;margin-bottom:10px;transition: transform 0.3s ease;" /></center>
        <p style="color:#0b6a7e;font-weight:500;">Transform your complex data into valuable insights through interactive, visual dashboards. We design real-time, custom dashboard solutions to help you make smarter, data-driven business decisions.</p>
        <div class="grid grid-cols-2 gap-4">
          <div>
          <ul>
          <li>✅ Interactive Data Visualization</li>
          <li>✅ Real-time Analytics Dashboard</li>
          </ul>
          </div>
           <div>
            <ul>
            <li>✅ Custom Charts & Graphs</li>
            <li>✅ Business Intelligence Reports</li>
            </ul>
          </div>
        </div><br/>
        <center><button class="whatsapp-btn" data-service="datavisual">
        <svg class="whatsapp-icon" viewBox="0 0 24 24" fill="currentColor">
        <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.890-5.335 11.893-11.893A11.821 11.821 0 0020.886 3.488"/>
        </svg> CALL US</button>
        </center>
      `
    },
    {
      id: 'landingpage',
      title: 'Web Design & Landing Page',
      icon: '⬡',
      price: 'Start From 5jt IDR - 50jt IDR',
      content: `
      <center><img src="/Images/Landing Page.webp" style="width:80%;height:350px;margin-bottom:10px;transition: transform 0.3s ease;" /></center>
        <p style="color:#0b6a7e;font-weight:500;">Create a memorable first impression with stunning web design and landing pages. We focus on designing displays that are not only beautiful but also responsive, fast, and conversion-optimized to drive real results for your business.</p>
        <div class="grid grid-cols-2 gap-4">
          <div>
          <ul>
          <li>✅ Responsive Web Design</li>
          <li>✅ Conversion-Optimized Landing Pages</li>
          </ul>
          </div>
           <div>
            <ul>
            <li>✅ SEO-Friendly Structure</li>
            <li>✅ Fast Loading Performance</li>
            </ul>
          </div>
        </div><br/>
        <center><button class="whatsapp-btn" data-service="landingpage">
        <svg class="whatsapp-icon" viewBox="0 0 24 24" fill="currentColor">
        <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.890-5.335 11.893-11.893A11.821 11.821 0 0020.886 3.488"/>
        </svg> CALL US</button>
        </center>
      `
    },
    {
      id: 'marketing',
      title: 'Digital Marketing, SEO & Advertising',
      icon: '⬡',
      price: 'Start From 5jt IDR - 50jt IDR',
      content: `
      <center><img src="/Images/Digital Marketing.webp" style="width:80%;height:350px;margin-bottom:10px;transition: transform 0.3s ease;" /></center>
        <p style="color:#0b6a7e;font-weight:500;">Increase your online visibility and reach your target audience more effectively. Through a comprehensive digital marketing strategy, we optimize SEO, manage advertising, and build targeted campaigns to grow your business.</p>
        <div class="grid grid-cols-2 gap-4">
          <div>
          <ul>
          <li>✅ Search Engine Optimization (SEO)</li>
          <li>✅ Social Media Marketing</li>
          </ul>
          </div>
           <div>
            <ul>
            <li>✅ Google Ads & PPC Campaigns</li>
            <li>✅ Content Marketing Strategy</li>
            </ul>
          </div>
        </div><br/>
        <center><button class="whatsapp-btn" data-service="marketing">
        <svg class="whatsapp-icon" viewBox="0 0 24 24" fill="currentColor">
        <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.890-5.335 11.893-11.893A11.821 11.821 0 0020.886 3.488"/>
        </svg> CALL US</button>
        </center>
      `
    },
    {
      id: 'design',
      title: 'Design Branding & Content',
      icon: '⬡',
      price: 'Start From 5jt IDR - 50jt IDR',
      content: `
       <center><img src="/Images/Content Creative.webp" style="width:80%;height:350px;margin-bottom:10px;transition: transform 0.3s ease;" /></center>
       <p style="color:#0b6a7e;font-weight:500;">Build a strong and memorable brand identity with our creative design services. From logo creation and promotional materials to social media content, we help create consistent and engaging visuals to enhance your brand image.</p>
        <div class="grid grid-cols-2 gap-4">
          <div>
          <ul>
          <li>✅ Logo Design & Brand Identity</li>
          <li>✅ Social Media Content Creation</li>
          </ul>
          </div>
           <div>
            <ul>
            <li>✅ Marketing Materials Design</li>
            <li>✅ Professional Photography & Videography</li>
            </ul>
          </div>
        </div><br/>
        <center><button class="whatsapp-btn" data-service="design">
        <svg class="whatsapp-icon" viewBox="0 0 24 24" fill="currentColor">
        <path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51-.173-.008-.371-.01-.57-.01-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 01-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 01-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 012.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0012.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 005.683 1.448h.005c6.554 0 11.890-5.335 11.893-11.893A11.821 11.821 0 0020.886 3.488"/>
        </svg> CALL US</button>
        </center>
      `
    }
  ];
  
  let activeTab = 'website';
  let isMobile = false;
  
  // Check if mobile on mount
  onMount(() => {
    const checkMobile = () => {
      isMobile = window.innerWidth < 768;
    };
    
    checkMobile();
    window.addEventListener('resize', checkMobile);

    // Event delegation untuk menangani klik pada tombol WhatsApp
    const handleWhatsAppClick = (event) => {
      const whatsappBtn = event.target.closest('.whatsapp-btn');
      if (whatsappBtn) {
        const service = whatsappBtn.getAttribute('data-service');
        
        switch(service) {
          case 'website':
            openWhatsAppWebDevelopment();
            break;
          case 'mobile':
            openWhatsAppMobileAppDevelopment();
            break;
          case 'datavisual':
            openWhatsAppDataVisualDashboard();
            break;
          case 'landingpage':
            openWhatsAppLandingPage();
            break;
          case 'marketing':
            openWhatsAppDigitalMarketing();
            break;
          case 'design':
            openWhatsAppDesignBranding();
            break;
          default:
            console.log('Service not found');
        }
      }
    };

    // Tambahkan event listener ke document
    document.addEventListener('click', handleWhatsAppClick);
    
    return () => {
      window.removeEventListener('resize', checkMobile);
      document.removeEventListener('click', handleWhatsAppClick);
    };
  });
  
  function selectTab(tabId) {
    activeTab = tabId;
  }

  $: activeTabData = tabs.find(tab => tab.id === activeTab);
  $: activeTabContent = tabs.find(tab => tab.id === activeTab)?.content || '';
</script>

<Saos animation={'from-left 0.7s cubic-bezier(0.35, 0.5, 0.65, 0.95) both'}>
<div class="vertical-tabs-container">
  <!-- Tab Navigation -->
  <div class="tabs-nav" class:mobile={isMobile}>
    {#each tabs as tab}
      <button 
        class="tab-button" 
        class:active={activeTab === tab.id}
        on:click={() => selectTab(tab.id)}
      >
        <span class="tab-icon">{tab.icon}</span>
        <span class="tab-title">{tab.title}</span>
      </button>
    {/each}
  </div>
  
  <!-- Tab Content -->
  <div class="tab-content" class:mobile={isMobile}>
    <div class="content-header">  
      <h1 style="color:#0b6a7e;font-weight: 700;margin-bottom: 6px;margin-top: -16px;">We Create {tabs.find(tab => tab.id === activeTab)?.title} For You</h1>
     
       <Badge large color="blue" border><BookmarkSolid class="me-2.5 h-3.5 w-3.5" />
        {activeTabData?.price}
        </Badge>
    </div>
    <div class="content-body">
      {@html activeTabContent}
    </div>
  </div>
</div>
</Saos>

<style>
/**  Setting SAOS (Sveltekit Animation on Scroll)*/
 @keyframes -global-from-left {
  0% {
    transform: rotateX(50deg) translateX(-200vw) skewX(-50deg);
    opacity: 1;
  }
  100% {
    transform: rotateX(0deg) translateX(0) skewX(0deg);
    opacity: 1;
  }
}

/** End Setting SAOS */

  .vertical-tabs-container {
    display: flex;
    min-height: 500px;
    max-width: 1200px;
    margin: 0 auto;
    border-radius: 16px;
    overflow: hidden;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  }
  
  .tabs-nav {
    background: white;
    border-right: 1px solid #e2e8f0;
    min-width: 280px;
    padding: 20px 0;
    display: flex;
    flex-direction: column;
    gap: 8px;
  }
  
  .tabs-nav.mobile {
    min-width: 100%;
    flex-direction: row;
    overflow-x: auto;
    border-right: none;
    border-bottom: 1px solid #e2e8f0;
    padding: 16px;
    gap: 12px;
  }
  
  .tab-button {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 16px 24px;
    margin: 0 16px;
    border: 2px solid transparent;
    border-radius: 12px;
    background: transparent;
    cursor: pointer;
    transition: all 0.2s ease;
    text-align: left;
    font-size: 16px;
    font-weight: 500;
    color: #64748b;
    min-width: fit-content;
  }
  
  .tab-button:hover {
    background: #f8fafc;
    border-color: #e2e8f0;
  }
  
  .tab-button.active {
    background: #dbeafe;
    border-color: #00a5c8;
    color: #1f2937;
    box-shadow: 0 2px 8px rgba(34, 75, 197, 0.1);
 }
 
 .tab-icon {
   font-size: 20px;
   color: #00a5c8;
   flex-shrink: 0;
 }
 
 .tab-title {
   flex: 1;
   white-space: nowrap;
   font-weight: 700;
 }
 
 .tab-content {
   flex: 1;
   background: #eef2ff;
   padding: 32px;
   overflow-y: auto;
 }
 
 .tab-content.mobile {
   padding: 24px 16px;
 }
 
 .content-header {
   margin-bottom: 24px;
   padding-bottom: 16px;
   border-bottom: 1px solid #50a2ff;
 }
 
 .content-header h1 {
   font-size: 24px;
   font-weight: 600;
   color: #1f2937;
   margin: 0;
 }
 
 .content-body {
   line-height: 1.6;
   color: #374151;
 }
 
 .content-body :global(h2) {
   font-size: 20px;
   font-weight: 600;
   color: #1f2937;
   margin-bottom: 16px;
 }
 
 .content-body :global(p) {
   margin-bottom: 16px;
   color: #6b7280;
 }
 
 .content-body :global(ul) {
   margin-bottom: 16px;
   margin-left:0px;
   margin-top:-8px;
   font-weight:500;
   line-height: 1.1;
 }
 
 .content-body :global(li) {
   margin-bottom: 8px;
   color:#0b6a7e;
 }

 :global(img:hover) {
		transform: scale(1.02);
	}
 
 /* Mobile Responsiveness */
 @media (max-width: 768px) {
   .vertical-tabs-container {
     flex-direction: column;
     margin: 16px;
     border-radius: 12px;
   }
   
   .tabs-nav {
     border-right: none;
     border-bottom: 1px solid #e2e8f0;
     min-width: 100%;
     flex-direction: row;
     overflow-x: auto;
     padding: 16px;
     gap: 12px;
   }
   
   .tab-button {
     margin: 0;
     padding: 12px 16px;
     min-width: fit-content;
     flex-shrink: 0;
   }
   
   .tab-title {
     font-size: 14px;
   }
   
   .content-header h1 {
     font-size: 20px;
   }
 }
 
 /* Tablet Responsiveness */
 @media (max-width: 1024px) and (min-width: 769px) {
   .tabs-nav {
     min-width: 240px;
   }
   
   .tab-button {
     padding: 14px 20px;
     margin: 0 12px;
   }
   
   .tab-content {
     padding: 24px;
   }
 }
 
 /* Custom scrollbar for mobile tabs */
 .tabs-nav.mobile::-webkit-scrollbar {
   height: 4px;
 }
 
 .tabs-nav.mobile::-webkit-scrollbar-track {
   background: #f1f5f9;
 }
 
 .tabs-nav.mobile::-webkit-scrollbar-thumb {
   background: #cbd5e1;
   border-radius: 4px;
 }
 
 .tabs-nav.mobile::-webkit-scrollbar-thumb:hover {
   background: #94a3b8;
 }

/* CSS Button Call Us */
 :global(.whatsapp-btn) {
   display: inline-flex;
   align-items: center;
   gap: 10px;
   background: linear-gradient(135deg, #25D366 0%, #128C7E 100%);
   color: white;
   border: none;
   padding: 14px 24px;
   border-radius: 30px;
   font-weight: 600;
   font-size: 16px;
   cursor: pointer;
   transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
   box-shadow: 0 4px 15px rgba(37, 211, 102, 0.3);
   text-decoration: none;
   position: relative;
   overflow: hidden;
 }

 :global(.whatsapp-btn::before) {
   content: '';
   position: absolute;
   top: 0;
   left: -100%;
   width: 100%;
   height: 100%;
   background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
   transition: left 0.5s;
 }

 :global(.whatsapp-btn:hover::before) {
   left: 100%;
 }

 :global(.whatsapp-btn:hover) {
   transform: translateY(-3px);
   box-shadow: 0 8px 25px rgba(37, 211, 102, 0.4);
 }

 :global(.whatsapp-btn:active) {
   transform: translateY(-1px);
 }

 :global(.whatsapp-icon) {
   width: 22px;
   height: 22px;
   flex-shrink: 0;
 }
</style>