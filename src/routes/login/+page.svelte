<script>
  let email = '';
  let password = '';
  
  function handleLogin() {
    console.log('Login attempt:', { email, password });
    // Tambahkan logika login di sini
  }
</script>

<div class="container">
  <div class="login-card">
    <div class="logo">
      <div class="logo-circles">
        <div class="circle circle-1"></div>
        <div class="circle circle-2"></div>
      </div>
    </div>
    
    <div class="form-section">
      <h1>LOGIN</h1>
      
      <form on:submit|preventDefault={handleLogin}>
        <div class="input-group">
          <input 
            type="email" 
            placeholder="Email" 
            bind:value={email}
            required
          />
        </div>
        
        <div class="input-group">
          <input 
            type="password" 
            placeholder="Password" 
            bind:value={password}
            required
          />
        </div>
        
        <button type="submit" class="login-btn">
          Login
        </button>
      </form>
    </div>
  </div>
</div>

<style>
  .container {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #f5f5f5;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  }

  .login-card {
    display: flex;
    background: white;
    border-radius: 12px;
    box-shadow: 0 10px 40px rgba(0, 0, 0, 0.1);
    overflow: hidden;
    width: 800px;
    max-width: 90vw;
    min-height: 500px;
  }

  .logo {
    flex: 1;
    background: linear-gradient(135deg, #e8f0ff 0%, #c8d9f5 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
  }

  .logo-circles {
    position: relative;
    width: 120px;
    height: 120px;
  }

  .circle {
    position: absolute;
    border-radius: 50%;
    background: rgba(255, 255, 255, 0.3);
    backdrop-filter: blur(10px);
  }

  .circle-1 {
    width: 80px;
    height: 80px;
    top: 0;
    left: 0;
    background: rgba(180, 200, 230, 0.6);
  }

  .circle-2 {
    width: 100px;
    height: 100px;
    bottom: 0;
    right: 0;
    background: rgba(160, 180, 220, 0.5);
  }

  .form-section {
    flex: 1;
    padding: 60px 50px;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  h1 {
    font-size: 28px;
    font-weight: 600;
    color: #333;
    margin-bottom: 40px;
    text-align: left;
  }

  .input-group {
    margin-bottom: 20px;
  }

  input {
    width: 100%;
    padding: 16px 20px;
    border: 2px solid #e1e5e9;
    border-radius: 8px;
    font-size: 16px;
    transition: border-color 0.3s ease;
    box-sizing: border-box;
  }

  input:focus {
    outline: none;
    border-color: #4285f4;
  }

  input::placeholder {
    color: #9ca3af;
  }

  .login-btn {
    width: 100%;
    padding: 16px;
    background: linear-gradient(135deg, #4285f4 0%, #1a73e8 100%);
    color: white;
    border: none;
    border-radius: 8px;
    font-size: 16px;
    font-weight: 500;
    cursor: pointer;
    transition: transform 0.2s ease, box-shadow 0.2s ease;
    margin-top: 10px;
  }

  .login-btn:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 25px rgba(66, 133, 244, 0.3);
  }

  .login-btn:active {
    transform: translateY(0);
  }

  @media (max-width: 768px) {
    .login-card {
      flex-direction: column;
      width: 100%;
      margin: 20px;
      max-width: calc(100vw - 40px);
    }
    
    .logo {
      min-height: 200px;
    }
    
    .form-section {
      padding: 40px 30px;
    }
  }
</style>