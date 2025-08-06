<script>
  import { onMount } from 'svelte';
  
  const words = ['Web Development', 'Mobile App Development ', 'Digital Marketing', 'Visual Data Dashboard'];
  
  let currentWordIndex = 0;
  let currentText = '';
  let isTyping = true;
  let charIndex = 0;
  
  const typeSpeed = 100; // kecepatan mengetik (ms)
  const deleteSpeed = 50; // kecepatan menghapus (ms)
  const pauseDuration = 2000; // jeda setelah selesai mengetik (ms)
  
  function typeWriter() {
    const currentWord = words[currentWordIndex];
    
    if (isTyping) {
      // Proses mengetik
      if (charIndex < currentWord.length) {
        currentText = currentWord.slice(0, charIndex + 1);
        charIndex++;
        setTimeout(typeWriter, typeSpeed);
      } else {
        // Selesai mengetik, tunggu sebentar lalu mulai menghapus
        setTimeout(() => {
          isTyping = false;
          typeWriter();
        }, pauseDuration);
      }
    } else {
      // Proses menghapus
      if (charIndex > 0) {
        currentText = currentWord.slice(0, charIndex - 1);
        charIndex--;
        setTimeout(typeWriter, deleteSpeed);
      } else {
        // Selesai menghapus, pindah ke kata berikutnya
        isTyping = true;
        currentWordIndex = (currentWordIndex + 1) % words.length;
        setTimeout(typeWriter, typeSpeed);
      }
    }
  }
  
  onMount(() => {
    typeWriter();
  });
</script>

<div class="typewriter-container">
  <span class="typewriter-text">{currentText}</span>
  <span class="cursor">|</span>
</div>

<style>
  .typewriter-container {
   /** font-family: 'Courier New', monospace;
    font-size: 2rem;
    font-weight: bold;
    color: #333;
    */
    display: inline-flex;
    align-items: center;
  }
  
  .typewriter-text {
    min-height: 1em;
  }
  
  .cursor {
    animation: blink 1s infinite;
    color: #007acc;
    margin-left: 2px;
  }
  
  @keyframes blink {
    0%, 50% {
      opacity: 1;
    }
    51%, 100% {
      opacity: 0;
    }
  }
</style>