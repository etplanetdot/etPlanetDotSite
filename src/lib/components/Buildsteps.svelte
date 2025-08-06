<script>
 import Saos from "saos";

  const stepsBuild = [
    {
      number: "01",
      title: "Research and analytics",
      description: "In-depth research on target audience, competitor analysis, and business needs audit to build the right strategy.",
      imgSrc: "/Images/Research and Analytics.webp" // ganti dengan path gambar Anda
    },
    {
      number: "02",
      title: "Design and Develop",
      description: "Creating attractive UI/UX designs and developing responsive websites/mobile apps according to your business needs.",
      imgSrc: "/Images/Design and Develop.webp" // ganti dengan path gambar Anda
    },
    {
      number: "03",
      title: "Deploy and Launch",
      description: "Official launch with performance optimization, team training, and digital marketing strategy implementation for maximum results.",
      imgSrc: "/Images/Deploy and Launch.webp" // ganti dengan path gambar Anda
    }
		
  ];
</script>

  
<div class="container">
  {#each stepsBuild as step}
  <Saos animation={'tilt-in-fwd-tr 0.6s cubic-bezier(0.250, 0.460, 0.450, 0.940) both'}
animation_out={'flip-out-hor-top 0.45s cubic-bezier(0.550, 0.085, 0.680, 0.530) both'} top={250}
bottom={250}>
    <div class="step">
      <div class="number">{step.number}</div>
      <div class="title">{step.title}</div>
      <div class="description">{step.description}</div>
      <img src={step.imgSrc} alt={step.title} />
    </div>
     </Saos>
  {/each}
</div>


<style>
/**  Setting SAOS (Sveltekit Animation on Scroll)*/
  @keyframes -global-tilt-in-fwd-tr {
  0% {
    transform: rotateX(20deg) translateX(100px) translateZ(-300px);
    opacity: 0;
  }
  100% {
    transform: rotateX(0deg) translateX(0) translateZ(0);
    opacity: 1;
  }
}

/** End Setting SAOS*/

  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 2rem 1rem;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 3rem;
  }

  .step {
    font-family: system-ui, sans-serif;
    background: #eef2ff;
    border-radius: 24px;
    padding: 2px 12px;
  }

  .number {
    font-size: 4rem;
    font-weight: 700;
    color: #ccc;
    position: relative;
    user-select: none;
    margin-bottom: 0.5rem;
    color: #cbe3ff;
    text-shadow: 6px 6px 8px #e5f1ff;
  }

  .title {
    font-size: 1.25rem;
    font-weight: 700;
    line-height: 1.3;
    margin-bottom: 0.75rem;
    margin-top: -60px;
    position: absolute;
    width: 140px;
    margin-left: 40px;
  }

  .description {
    font-size: 0.9rem;
    color: #888;
    line-height: 1.4;
    min-height: 3.4rem;
    margin-bottom:8px;
  }

  img {
    width: 100%;
    height: 180px;
    border-radius: 40px;
    box-shadow: rgb(44 54 61 / 10%) 10px 10px, rgb(38 77 105 / 5%) 15px 15px;
    transition: transform 0.3s ease;
  }

  img:hover {
		transform: scale(1.02);
	}

  @media(max-width: 900px) {
    .container {
      grid-template-columns: 1fr;
    }
    .step {
      margin-bottom: 3rem;
    }
    .number {
      font-size: 3rem;
    }
  }
</style>