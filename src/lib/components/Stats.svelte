<script>
import Saos from "saos";

 const stats = [
   { label: 'Since', value: '2017', icon: '📅' },
   { label: 'Project', value: '50+', icon: '📊' },
   { label: 'Client', value: '60+', icon: '👥' },
   { label: 'Satisfaction Score', value: '100%', icon: '🏆' }
 ];
</script>

<main>
 <Saos animation={'scale-in-center 0.5s cubic-bezier(0.250, 0.460, 0.450, 0.940) both'}>
 <div class="stats-container">
   {#each stats as stat, index}
     <div class="stat-card" style="--delay: {index * 0.1}s">
       <div class="label">{stat.label}</div>
       <div class="content">
         <span class="icon">{stat.icon}</span>
         <span class="value">{stat.value}</span>
       </div>

     </div>
   {/each}
 </div>
 </Saos>
</main>

<style>

/**  Setting SAOS (Sveltekit Animation on Scroll)*/
   @keyframes -global-from-left {
    0% {
      transform: translateX(-200vw);
      opacity: 0;
    }
    100% {
      transform: translateX(0);
      opacity: 1;
    }
  }

/** End Setting SAOS*/

 main {
   display: flex;
   align-items: center;
   justify-content: center;
   font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
 }

 .stats-container {
   display: grid;
   grid-template-columns: repeat(4, 1fr);
   gap: 2rem;
   max-width: 1100px;
   width: 100%;
 }

 .stat-card {
   background: white;
   border-radius: 12px;
   padding: 0.7rem 1.1rem;
   border: 1px solid #f1f5f9;
   transition: all 0.3s ease;
   opacity: 0;
   transform: translateY(20px);
   animation: slideUp 0.5s ease forwards;
   animation-delay: var(--delay);
   position: relative;
   min-height: 80px;
   box-shadow: rgba(0, 0, 0, 0.45) 0px 25px 20px -20px;
   width: 240px;
 }

 .stat-card:hover {
   transform: translateY(-4px);
   box-shadow: 
     0 8px 20px rgba(0, 0, 0, 0.08),
     0 2px 6px rgba(0, 0, 0, 0.12);
 }

 .label {
   font-size: 0.75rem;
   font-weight: 600;
   color: #64748b;
   text-transform: uppercase;
   letter-spacing: 0.5px;
    margin-bottom: 0.5rem;
    padding: 2px 16px;
    width: max-content;
    color: white;
 }

 .content {
   display: flex;
   align-items: center;
   gap: 0.75rem;
   margin-bottom: 0.75rem;
 }

 .icon {
    font-size: 1.5rem;
    opacity: 0.8;
    padding: 3px;
    background-color: #c9e6dc;
    border-radius: 8px;
 }

 .value {
   font-size: 1.8rem;
   font-weight: 800;
   line-height: 1;
 }

 .stat-card:nth-child(1) .value {
   color: #00c99c;
 }

 .stat-card:nth-child(2) .value {
   color: #00b7b5;
 }

 .stat-card:nth-child(3) .value {
   color: #00a5c8;
 }

 .stat-card:nth-child(4) .value {
   color: #006cf4;
 }

 .stat-card:nth-child(1) .label {
    background: #00c99c;
    text-shadow: 1px 1px 4px #00c99c;
 }

 .stat-card:nth-child(2) .label {
    background: #00b7b5;
    text-shadow: 1px 1px 4px #00b7b5;
 }

 .stat-card:nth-child(3) .label {
    background: #00a5c8;
    text-shadow: 1px 1px 4px #00a5c8;
 }

 .stat-card:nth-child(4) .label {
    background: #006cf4;
    text-shadow: 1px 1px 4px #006cf4;
 }



 @keyframes slideUp {
   to {
     opacity: 1;
     transform: translateY(0);
   }
 }

 @media (max-width: 768px) {
   .stats-container {
     grid-template-columns: repeat(2, 1fr);
     gap: 0.75rem;
   }
 }

 @media (max-width: 480px) {
   .stats-container {
     grid-template-columns: 1fr;
     max-width: 300px;
   }
   
   .stat-card {
     padding: 0.75rem 1rem;
   }
   
   .value {
     font-size: 1.5rem;
   }
 }
</style>