<script>
  // Importamos los estilos necesarios
  import { onMount } from 'svelte';
  
  // Variables para controlar estados si es necesario
  let isMenuOpen = false;
  let isAnnualPlan = true;
  
  // Precios mensuales y anuales
  const prices = {
    starter: {
      monthly: 14.99,
      annual: 14.99
    },
    medium: {
      monthly: 22.99,
      annual: 22.99
    },
    plus: {
      monthly: 43.99,
      annual: 43.99
    }
  };
  
  // Función para alternar el menú en dispositivos móviles si es necesario
  const toggleMenu = () => {
    isMenuOpen = !isMenuOpen;
  };
  
  // Función para alternar entre planes mensuales y anuales
  const togglePlanType = () => {
    isAnnualPlan = !isAnnualPlan;
  };
  
  // Función para formatear precios
  const formatPrice = (price) => {
    return price.toFixed(2).replace('.', ',');
  };
</script>

<svelte:head>
  <title>Agendora - Organiza y gestiona tus tiempos</title>
  <meta name="description" content="Haz que las citas en tu negocio fluyan sin esfuerzo, para cualquier emprendimiento o negocio" />
</svelte:head>

<main>
  <!-- Barra de navegación -->
  <nav class="navbar">
    <div class="logo">
      <a href="/">
        <img src="/logo.svg" alt="Agendora" />
      </a>
    </div>
    
    <div class="nav-links">
      <a href="/">Home</a>
      <a href="/funcionalidades">Funcionalidades</a>
      <a href="/beneficios">Beneficios</a>
      <a href="/pricing">Pricing</a>
    </div>
    
    <div class="auth-buttons">
      <a href="/iniciar-sesion" class="login-btn">Iniciar sesión</a>
      <a href="/solicitar-demo" class="demo-btn">Solicitar una demo</a>
    </div>
  </nav>

  <!-- Hero Section -->
  <section class="hero">
    <div class="hero-badge">
      <span>Nuevo</span>
      <span>Portal de conversión</span>
    </div>
    
    <h1 class="hero-title">
      <span class="dark-text">Organizá y gestioná</span>
      <span class="light-text">tus tiempos.</span>
    </h1>
    
    <p class="hero-subtitle">
      Haz que las citas en tu negocio fluyan sin esfuerzo, 
      <span class="highlight">para cualquier emprendimiento o negocio</span>, 
      en cualquier momento y desde cualquier lugar
    </p>
    
    <div class="hero-buttons">
      <a href="/registro" class="register-btn">Registrate ahora</a>
      <a href="/demo-gratis" class="free-demo-btn">Solicita una demo gratis</a>
    </div>
    
    <!-- Divisor rojo para la imagen -->
    <div class="image-placeholder"></div>
  </section>

  <!-- Sección Whatsapp -->
  <section class="whatsapp-section">
    <div class="whatsapp-content">
      <h2 class="whatsapp-title">
        Automatiza y agiliza tus respuestas en Whatsapp en <span class="highlight-blue">"1 clic"</span>.
      </h2>
      
      <p class="whatsapp-description">
        Aprovechamos la comodidad de tus clientes, desde nuestra aplicación, podrás gestionar las conversaciones, automatizar respuestas y organizar tus agendas asignando días y horarios fácilmente.
      </p>
      
      <ul class="features-list">
        <li class="feature-item">
          <span class="feature-icon">
            <img src="/calendar-icon.svg" alt="Calendario" />
          </span>
          <span class="feature-text">99.99% de cumplimiento del SLA, de lunes a domingo.</span>
        </li>
        <li class="feature-item">
          <span class="feature-icon">
            <img src="/user-icon.svg" alt="Usuario" />
          </span>
          <span class="feature-text">Almacena tus clientes, nombre, email, telefono, etc</span>
        </li>
        <li class="feature-item">
          <span class="feature-icon">
            <img src="/message-icon.svg" alt="Mensaje" />
          </span>
          <span class="feature-text">Envía mensajes de seguimiento a tus clientes</span>
        </li>
      </ul>
    </div>
    
    <div class="whatsapp-image-container">
      <!-- Divisor rojo para la imagen principal -->
      <div class="whatsapp-image"></div>
      
      <!-- Recuadro burdeo para la segunda imagen -->
      <div class="whatsapp-overlay-image"></div>
    </div>
  </section>

  <!-- Sección de Planes -->
  <section class="pricing-section">
    <h2 class="pricing-title">Selecciona tu plan</h2>
    
    <div class="pricing-toggle">
      <span class={!isAnnualPlan ? 'toggle-option active' : 'toggle-option'}>Mensual</span>
      <label class="toggle-switch">
        <input type="checkbox" checked={isAnnualPlan} on:change={togglePlanType} />
        <span class="toggle-slider"></span>
      </label>
      <span class={isAnnualPlan ? 'toggle-option active' : 'toggle-option'}>Anual</span>
    </div>
    
    <div class="pricing-cards">
      <!-- Plan Starter -->
      <div class="pricing-card">
        <div class="card-header">
          <h3 class="card-title">Starter</h3>
          <p class="card-subtitle">Remote acces essentials for athome users and testing</p>
        </div>
        
        <div class="card-price">
          <span class="price-amount">${isAnnualPlan ? formatPrice(prices.starter.annual) : formatPrice(prices.starter.monthly)}</span>
        </div>
        
        <a href="/registro" class="trial-btn">
          14 Días gratis
          <img src="/arrow-right-icon.svg" alt="Flecha derecha" class="icon-small" />
        </a>
        
        <p class="card-note">No necesitas una tarjeta de crédito</p>
        
        <ul class="card-features">
          <li class="card-feature">
            <img src="/check-icon.svg" alt="Check" class="icon-small" />
            Up to 5 users
          </li>
          <li class="card-feature">
            <img src="/check-icon.svg" alt="Check" class="icon-small" />
            Up to 5 users
          </li>
        </ul>
      </div>
      
      <!-- Plan Medium -->
      <div class="pricing-card featured">
        <div class="card-badge">MÁS VENDIDO</div>
        <div class="card-header">
          <h3 class="card-title">Medium</h3>
          <p class="card-subtitle">Remote acces essentials for athome users and testing</p>
        </div>
        
        <div class="card-price">
          <span class="price-amount">${isAnnualPlan ? formatPrice(prices.medium.annual) : formatPrice(prices.medium.monthly)}</span>
        </div>
        
        <a href="/registro" class="trial-btn">
          14 Días gratis
          <img src="/arrow-right-icon.svg" alt="Flecha derecha" class="icon-small" />
        </a>
        
        <p class="card-note">No necesitas una tarjeta de crédito</p>
        
        <ul class="card-features">
          <li class="card-feature">
            <img src="/check-icon.svg" alt="Check" class="icon-small" />
            Up to 5 users
          </li>
          <li class="card-feature">
            <img src="/check-icon.svg" alt="Check" class="icon-small" />
            Up to 5 users
          </li>
        </ul>
      </div>
      
      <!-- Plan Plus+ -->
      <div class="pricing-card">
        <div class="card-header">
          <h3 class="card-title">
            <img src="/star-icon.svg" alt="Estrella" class="icon-small" />
            Plus+
          </h3>
          <p class="card-subtitle">Remote acces essentials for athome users and testing</p>
        </div>
        
        <div class="card-price">
          <span class="price-amount">${isAnnualPlan ? formatPrice(prices.plus.annual) : formatPrice(prices.plus.monthly)}</span>
        </div>
        
        <a href="/registro" class="trial-btn">
          14 Días gratis
          <img src="/arrow-right-icon.svg" alt="Flecha derecha" class="icon-small" />
        </a>
        
        <p class="card-note">No necesitas una tarjeta de crédito</p>
        
        <ul class="card-features">
          <li class="card-feature">
            <img src="/check-icon.svg" alt="Check" class="icon-small" />
            Up to 5 users
          </li>
          <li class="card-feature">
            <img src="/check-icon.svg" alt="Check" class="icon-small" />
            Up to 5 users
          </li>
        </ul>
      </div>
    </div>
  </section>

  <!-- Sección Software Intuitivo -->
  <section class="software-section">
    <!-- Divisor rojo para la imagen (ahora ocupa la mitad izquierda) -->
    <div class="software-image"></div>
    
    <div class="software-content">
      <h2 class="software-title">Usa software intuitivo en vez de procesos manuales.</h2>
      
      <p class="software-description">
        Optimiza tu flujo de trabajo reemplazando tediosos procesos manuales con un software intuitivo diseñado para simplificar tareas, ahorrar tiempo y aumentar la eficiencia en cada paso.
      </p>
      
      <a href="/registro" class="register-btn software-btn">
        Regístrate ahora
        <img src="/arrow-right-icon.svg" alt="Flecha derecha" class="icon-small" />
      </a>
    </div>
  </section>
</main>

<!-- Footer -->
<footer class="footer">
  <div class="footer-container">
    <div class="footer-columns">
      <div class="footer-column">
        <h3 class="footer-title">Acceso rápido</h3>
        <ul class="footer-links">
          <li><a href="/crear-cuenta">Crear cuenta</a></li>
          <li><a href="/iniciar-sesion">Iniciar Sesión</a></li>
          <li><a href="/pricing">Precios</a></li>
          <li><a href="/blog">Blog</a></li>
        </ul>
      </div>
      
      <div class="footer-column">
        <h3 class="footer-title">Agendora</h3>
        <ul class="footer-links">
          <li><a href="/">Home</a></li>
          <li><a href="/funcionalidades">Funcionalidades</a></li>
          <li><a href="/beneficios">Beneficios</a></li>
          <li><a href="/pricing">Pricing</a></li>
        </ul>
      </div>
    </div>
    
    <div class="footer-bottom">
      <p class="copyright">© 2023 Agendora. Todos los derechos reservados.</p>
      
      <div class="social-links">
        <a href="https://facebook.com" class="social-link" aria-label="Facebook">
          <img src="/facebook-icon.svg" alt="Facebook" class="social-icon" />
        </a>
        <a href="https://instagram.com" class="social-link" aria-label="Instagram">
          <img src="/instagram-icon.svg" alt="Instagram" class="social-icon" />
        </a>
        <a href="https://linkedin.com" class="social-link" aria-label="LinkedIn">
          <img src="/linkedin-icon.svg" alt="LinkedIn" class="social-icon" />
        </a>
        <a href="https://twitter.com" class="social-link" aria-label="Twitter">
          <img src="/twitter-icon.svg" alt="Twitter" class="social-icon" />
        </a>
      </div>
    </div>
  </div>
</footer>

<style>
  /* Estilos generales */
  :global(body) {
    margin: 0;
    padding: 0;
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    background: linear-gradient(to bottom, #f0f4ff, #e6f0ff);
  }
  
  main {
    width: 100%;
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 1rem;
  }
  
  /* Barra de navegación */
  .navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1.5rem 0;
  }
  
  .logo img {
    height: 2rem;
  }
  
  .nav-links {
    display: flex;
    gap: 2rem;
  }
  
  .nav-links a {
    text-decoration: none;
    color: #333;
    font-weight: 500;
    transition: color 0.2s;
  }
  
  .nav-links a:hover {
    color: #4285f4;
  }
  
  .auth-buttons {
    display: flex;
    gap: 1rem;
    align-items: center;
  }
  
  .login-btn {
    color: #4285f4;
    text-decoration: none;
    font-weight: 500;
  }
  
  .demo-btn {
    background-color: #0052ff;
    color: white;
    padding: 0.75rem 1.5rem;
    border-radius: 2rem;
    text-decoration: none;
    font-weight: 500;
    transition: background-color 0.2s;
  }
  
  .demo-btn:hover {
    background-color: #0045db;
  }
  
  /* Hero Section */
  .hero {
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    padding: 3rem 0;
  }
  
  .hero-badge {
    display: inline-flex;
    align-items: center;
    background-color: rgba(66, 133, 244, 0.1);
    border-radius: 2rem;
    padding: 0.5rem 1rem;
    margin-bottom: 2rem;
    gap: 0.5rem;
  }
  
  .hero-badge span:first-child {
    background-color: #4285f4;
    color: white;
    padding: 0.25rem 0.75rem;
    border-radius: 1rem;
    font-size: 0.875rem;
    font-weight: 500;
  }
  
  .hero-badge span:last-child {
    color: #4285f4;
    font-size: 0.875rem;
    font-weight: 500;
  }
  
  .hero-title {
    font-size: 3.5rem;
    font-weight: 800;
    margin-bottom: 1.5rem;
    line-height: 1.2;
  }
  
  .dark-text {
    color: #333;
  }
  
  .light-text {
    color: #4285f4;
  }
  
  .hero-subtitle {
    font-size: 1.25rem;
    color: #555;
    max-width: 800px;
    margin-bottom: 2.5rem;
    line-height: 1.5;
  }
  
  .highlight {
    color: #4285f4;
  }
  
  .hero-buttons {
    display: flex;
    gap: 1rem;
    margin-bottom: 3rem;
  }
  
  .register-btn {
    background-color: #0052ff;
    color: white;
    padding: 0.75rem 1.5rem;
    border-radius: 2rem;
    text-decoration: none;
    font-weight: 500;
    display: flex;
    align-items: center;
    gap: 0.5rem;
    transition: background-color 0.2s;
  }
  
  .register-btn:hover {
    background-color: #0045db;
  }
  
  .free-demo-btn {
    color: #4285f4;
    text-decoration: none;
    font-weight: 500;
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }
  
  /* Divisor rojo para la imagen */
  .image-placeholder {
    width: 100%;
    max-width: 900px;
    height: 400px;
    background-color: #ff0000;
    border-radius: 1rem;
    margin: 0 auto;
  }
  
  /* Sección Whatsapp */
  .whatsapp-section {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 5rem 0;
    gap: 2rem;
  }
  
  .whatsapp-content {
    flex: 1;
    max-width: 550px;
  }
  
  .whatsapp-title {
    font-size: 2.5rem;
    font-weight: 800;
    color: #333;
    margin-bottom: 1.5rem;
    line-height: 1.2;
  }
  
  .highlight-blue {
    color: #4285f4;
  }
  
  .whatsapp-description {
    font-size: 1.125rem;
    color: #555;
    margin-bottom: 2rem;
    line-height: 1.6;
  }
  
  .features-list {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  
  .feature-item {
    display: flex;
    align-items: center;
    margin-bottom: 1.25rem;
    font-size: 1rem;
    color: #555;
  }
  
  .feature-icon {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 2rem;
    height: 2rem;
    margin-right: 1rem;
    background-color: rgba(66, 133, 244, 0.1);
    border-radius: 0.25rem;
    padding: 0.25rem;
  }
  
  .feature-icon img {
    width: 100%;
    height: 100%;
  }
  
  .whatsapp-image-container {
    flex: 1;
    position: relative;
    height: 400px;
  }
  
  .whatsapp-image {
    width: 100%;
    height: 100%;
    background-color: #ff0000;
    border-radius: 1rem;
    position: relative;
  }
  
  .whatsapp-overlay-image {
    position: absolute;
    top: -50px;
    right: 50px;
    width: 300px;
    height: 150px;
    background-color: #8B0000; /* Rojo oscuro/burdeo */
    border-radius: 0.5rem;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
  }
  
  /* Sección de Planes */
  .pricing-section {
    padding: 5rem 0;
    text-align: center;
  }
  
  .pricing-title {
    font-size: 2.5rem;
    font-weight: 800;
    color: #333;
    margin-bottom: 2rem;
  }
  
  .pricing-toggle {
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 3rem;
    gap: 1rem;
  }
  
  .toggle-option {
    font-size: 1rem;
    color: #555;
    font-weight: 500;
  }
  
  .toggle-option.active {
    color: #4285f4;
  }
  
  .toggle-switch {
    position: relative;
    display: inline-block;
    width: 50px;
    height: 24px;
  }
  
  .toggle-switch input {
    opacity: 0;
    width: 0;
    height: 0;
  }
  
  .toggle-slider {
    position: absolute;
    cursor: pointer;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: #4285f4;
    transition: .4s;
    border-radius: 34px;
  }
  
  .toggle-slider:before {
    position: absolute;
    content: "";
    height: 16px;
    width: 16px;
    left: 4px;
    bottom: 4px;
    background-color: white;
    transition: .4s;
    border-radius: 50%;
  }
  
  .toggle-switch input:checked + .toggle-slider:before {
    transform: translateX(26px);
  }
  
  .pricing-cards {
    display: flex;
    justify-content: center;
    gap: 1.5rem;
    margin-top: 2rem;
  }
  
  .pricing-card {
    background-color: #1a1a1a;
    border-radius: 0.75rem;
    padding: 2rem;
    width: 100%;
    max-width: 300px;
    text-align: left;
    color: white;
    position: relative;
    display: flex;
    flex-direction: column;
  }
  
  .pricing-card.featured {
    border: 2px solid #4285f4;
  }
  
  .card-badge {
    position: absolute;
    top: -12px;
    right: 20px;
    background-color: #4285f4;
    color: white;
    font-size: 0.75rem;
    font-weight: 600;
    padding: 0.25rem 0.75rem;
    border-radius: 1rem;
  }
  
  .card-header {
    margin-bottom: 1.5rem;
  }
  
  .card-title {
    font-size: 1.5rem;
    font-weight: 700;
    margin-bottom: 0.5rem;
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }
  
  .card-subtitle {
    font-size: 0.875rem;
    color: #aaa;
    line-height: 1.4;
  }
  
  .card-price {
    margin-bottom: 1.5rem;
  }
  
  .price-amount {
    font-size: 2rem;
    font-weight: 700;
  }
  
  .trial-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 0.5rem;
    background-color: rgba(66, 133, 244, 0.1);
    color: #4285f4;
    padding: 0.75rem;
    border-radius: 0.5rem;
    font-weight: 500;
    margin-bottom: 1rem;
    transition: background-color 0.2s;
  }
  
  .trial-btn:hover {
    background-color: rgba(66, 133, 244, 0.2);
  }
  
  .card-note {
    font-size: 0.75rem;
    color: #aaa;
    margin-bottom: 1.5rem;
    text-align: center;
  }
  
  .card-features {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  
  .card-feature {
    display: flex;
    align-items: center;
    gap: 0.5rem;
    margin-bottom: 0.75rem;
    font-size: 0.875rem;
  }
  
  /* Sección Software Intuitivo */
  .software-section {
    display: flex;
    align-items: center;
    padding: 0;
    background-color: #4285f4;
    border-radius: 1rem;
    margin: 3rem 0;
    overflow: hidden;
  }
  
  .software-image {
    width: 50%;
    height: 400px;
    background-color: #ff0000;
    border-radius: 0;
  }
  
  .software-content {
    width: 50%;
    padding: 3rem;
    color: white;
  }
  
  .software-title {
    font-size: 2.25rem;
    font-weight: 800;
    margin-bottom: 1.5rem;
    line-height: 1.2;
  }
  
  .software-description {
    font-size: 1rem;
    margin-bottom: 2rem;
    line-height: 1.6;
    opacity: 0.9;
  }
  
  .software-btn {
    background-color: white;
    color: #4285f4;
    border: none;
  }
  
  .software-btn:hover {
    background-color: rgba(255, 255, 255, 0.9);
  }
  
  /* Footer */
  .footer {
    background-color: #4285f4;
    color: white;
    padding: 3rem 0 1.5rem;
    margin-top: 5rem;
  }
  
  .footer-container {
    width: 100%;
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 1rem;
  }
  
  .footer-columns {
    display: flex;
    justify-content: flex-start;
    gap: 4rem;
    margin-bottom: 3rem;
  }
  
  .footer-column {
    min-width: 150px;
  }
  
  .footer-title {
    font-size: 1.125rem;
    font-weight: 600;
    margin-bottom: 1.5rem;
  }
  
  .footer-links {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  
  .footer-links li {
    margin-bottom: 0.75rem;
  }
  
  .footer-links a {
    color: rgba(255, 255, 255, 0.8);
    text-decoration: none;
    font-size: 0.9rem;
    transition: color 0.2s;
  }
  
  .footer-links a:hover {
    color: white;
  }
  
  .footer-bottom {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding-top: 1.5rem;
    border-top: 1px solid rgba(255, 255, 255, 0.2);
  }
  
  .copyright {
    font-size: 0.875rem;
    color: rgba(255, 255, 255, 0.8);
  }
  
  .social-links {
    display: flex;
    gap: 1rem;
  }
  
  .social-link {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 2rem;
    height: 2rem;
    border-radius: 50%;
    background-color: rgba(255, 255, 255, 0.1);
    transition: background-color 0.2s;
  }
  
  .social-link:hover {
    background-color: rgba(255, 255, 255, 0.2);
  }
  
  .social-icon {
    width: 1rem;
    height: 1rem;
    filter: brightness(0) invert(1);
  }
  
  /* Responsive */
  @media (max-width: 768px) {
    .navbar {
      flex-direction: column;
      gap: 1rem;
    }
    
    .nav-links {
      flex-direction: column;
      align-items: center;
      gap: 1rem;
    }
    
    .hero-title {
      font-size: 2.5rem;
    }
    
    .hero-buttons {
      flex-direction: column;
    }
    
    .image-placeholder {
      height: 250px;
    }
    
    .whatsapp-section {
      flex-direction: column;
      padding: 3rem 0;
    }
    
    .whatsapp-content {
      max-width: 100%;
    }
    
    .whatsapp-title {
      font-size: 2rem;
    }
    
    .whatsapp-image-container {
      width: 100%;
      margin-top: 2rem;
    }
    
    .whatsapp-overlay-image {
      right: 20px;
      width: 200px;
    }
    
    .pricing-cards {
      flex-direction: column;
      align-items: center;
    }
    
    .pricing-card {
      max-width: 100%;
      margin-bottom: 1.5rem;
    }
    
    .software-section {
      flex-direction: column;
    }
    
    .software-image {
      width: 100%;
      height: 250px;
    }
    
    .software-content {
      width: 100%;
      padding: 2rem 1.5rem;
    }
    
    .software-title {
      font-size: 1.75rem;
    }
  }
  
  .icon-small {
    width: 16px;
    height: 16px;
  }
</style>
