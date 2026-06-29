<script>
    import FeaturedCards from "$lib/FeaturedCards.svelte";
    // Datos de los servicios basados en la cotización
    const serviciosRecurrentes = [
        {
            titulo: "Hosting 6GB",
            precio: "$80",
            periodo: "/anual",
            descripcion:
                "Hasta 100k visitas/mes, uptime 99.99%, SSL y backups diarios.",
        },
        {
            titulo: "Hosting Infinite 10GB",
            precio: "$100",
            periodo: "/anual",
            descripcion:
                "Hasta 100k visitas/mes, uptime 99.99%, SSL y backups diarios.",
        },
        {
            titulo: "Hosting Universe 16GB",
            precio: "$180",
            periodo: "/anual",
            descripcion:
                "Hasta 100k visitas/mes, uptime 99.99%, SSL y backups diarios.",
        },
        {
            titulo: "Dominio Web",
            precio: "$16",
            periodo: "/anual",
            descripcion: "Registro de dominio .com, .net u .org por un año.",
        },
        {
            titulo: "Correos Empresariales",
            precio: "$12",
            periodo: "/anual",
            descripcion:
                "3 cuentas de 1GB. Administración independiente o vía Gmail/Outlook.",
        },
    ];

    const serviciosDesarrollo = [
        {
            titulo: "Desarrollo Web WordPress - Mediano",
            precio: "$180",
            periodo: "pago único",
            descripcion:
                "Sitio web adaptable de 4 a 10 secciones. Incluye blog, formularios de contacto, iteraciones de diseño y guía de manejo.",
        },
        {
            titulo: "Desarrollo Web WordPress - Grande",
            precio: "$280",
            periodo: "pago único",
            descripcion:
                "Sitio web adaptable de 10 o más secciones. Incluye blog, formularios de contacto, iteraciones de diseño y guía de manejo.",
        },
        {
            titulo: "E-commerce & Membresías",
            precio: "$180",
            periodo: "pago único",
            descripcion:
                "Desarrollo de tienda en línea o funcionalidades avanzadas a medida.",
        },
    ];

    const portafolio = [
        { nombre: "Himchari TKD", url: "http://himcharitkd.com" },
        { nombre: "Pacto RCF", url: "http://pacto-rcf.com" },
        { nombre: "Hotel Mamallacta", url: "http://mamallacta.com" },
        { nombre: "Maigua Living", url: "http://maigualiving.com" },
    ];
</script>

<main>
    <header class="hero">
        <h2>Desarrollo y Alojamiento Web</h2>
        <h1>Por: Mauricio Cárdenas</h1>
        <p>
            Soluciones digitales minimalistas, rápidas y seguras para escalar tu
            negocio. Todo lo que necesitas, sin complicaciones.
        </p>
        <a href="#contacto" class="btn">Solicitar Cotización</a>
    </header>

    <FeaturedCards />

    <section class="section">
        <div class="section-header">
            <h3>Infraestructura & Alojamiento</h3>
            <p>
                La base sólida que tu sitio web necesita para estar siempre en
                línea.
            </p>
        </div>
        <div class="grid">
            {#each serviciosRecurrentes as servicio}
                <article class="card">
                    <h4>{servicio.titulo}</h4>
                    <div class="price">
                        <strong>{servicio.precio}</strong><span
                            >{servicio.periodo}</span
                        >
                    </div>
                    <p>{servicio.descripcion}</p>
                </article>
            {/each}
        </div>
    </section>

    <section class="section">
        <div class="section-header">
            <h3>Desarrollo a Medida</h3>
            <p>Diseño adaptable, consistente y autogestionable.</p>
        </div>
        <div class="grid">
            {#each serviciosDesarrollo as servicio}
                <article class="card dark">
                    <h4>{servicio.titulo}</h4>
                    <div class="price">
                        <strong>{servicio.precio}</strong><span>
                            / {servicio.periodo}</span
                        >
                    </div>
                    <p>{servicio.descripcion}</p>
                </article>
            {/each}
        </div>
    </section>

    <section class="section">
        <div class="section-header">
            <h3>Trabajos Recientes</h3>
        </div>
        <ul class="portfolio-list">
            {#each portafolio as item}
                <li>
                    <a
                        href={item.url}
                        target="_blank"
                        rel="noopener noreferrer"
                    >
                        {item.nombre} ↗
                    </a>
                </li>
            {/each}
        </ul>
    </section>

    <footer id="contacto">
        <div class="footer-content">
            <h3>¿Listo para empezar?</h3>
            <p>
                Soporte gratuito de por vida para clientes. Transparencia y
                confidencialidad garantizada.
            </p>
            <a href="https://wa.me/593984029541" class="btn outline">WhatsApp</a
            >
        </div>
    </footer>
</main>

<style>
    /* Configuración global y variables */
    :global(body) {
        margin: 0;
        padding: 0;
        background-color: #fafafa;
        color: #111111;
        font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
            Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        line-height: 1.6;
    }

    :root {
        --space-sm: 1rem;
        --space-md: 2rem;
        --space-lg: 4rem;
        --space-xl: 8rem;
        --radius: 8px;
        --border: 1px solid #eaeaea;
    }

    /* Layout base */
    main {
        max-width: 1200px;
        margin: 0 auto;
        padding: var(--space-md);
    }

    /* Hero Section */
    .hero {
        padding: var(--space-xl) 0 var(--space-lg);
        max-width: 700px;
    }

    .hero h1 {
        font-size: clamp(1.5rem, 4vw, 2rem);
        font-weight: 500;
        color: #666;
        margin: 0 0 0.5rem 0;
    }

    .hero h2 {
        font-size: clamp(2.5rem, 8vw, 4.5rem);
        font-weight: 700;
        letter-spacing: -0.03em;
        line-height: 1.1;
        margin: 0 0 var(--space-md) 0;
    }

    .hero p {
        font-size: clamp(1.1rem, 3vw, 1.25rem);
        color: #555;
        margin-bottom: var(--space-md);
    }

    /* Botones */
    .btn {
        display: inline-block;
        background: #111;
        color: #fff;
        text-decoration: none;
        padding: 1rem 2rem;
        border-radius: 100px; /* Estilo píldora muy moderno */
        font-weight: 500;
        transition:
            transform 0.2s ease,
            background 0.2s ease;
    }

    .btn:hover {
        background: #333;
        transform: translateY(-2px);
    }

    .btn.outline {
        background: transparent;
        color: #111;
        border: 1px solid #111;
    }

    .btn.outline:hover {
        background: #111;
        color: #fff;
    }

    /* Secciones y Grid Responsivo Integrado */
    .section {
        padding: var(--space-lg) 0;
        border-top: var(--border);
    }

    .section-header {
        margin-bottom: var(--space-md);
    }

    .section-header h3 {
        font-size: 1.5rem;
        margin: 0 0 0.5rem 0;
    }

    .section-header p {
        color: #666;
        margin: 0;
    }

    /* La magia de la responsividad con poco código */
    .grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(min(100%, 280px), 1fr));
        gap: var(--space-md);
    }

    /* Tarjetas de Servicio */
    .card {
        background: #fff;
        border: var(--border);
        padding: var(--space-md);
        border-radius: var(--radius);
        display: flex;
        flex-direction: column;
    }

    .card.dark {
        background: #111;
        color: #fff;
        border-color: #111;
    }

    .card h4 {
        margin: 0 0 1rem 0;
        font-size: 1.2rem;
        font-weight: 600;
    }

    .card .price {
        margin-bottom: 1rem;
        font-size: 1rem;
    }

    .card .price strong {
        font-size: 2rem;
        line-height: 1;
    }

    .card .price span {
        color: #888;
    }

    .card p {
        margin: 0;
        color: #666;
        font-size: 0.95rem;
    }

    .card.dark p {
        color: #aaa;
    }

    /* Lista del Portafolio */
    .portfolio-list {
        list-style: none;
        padding: 0;
        margin: 0;
        display: flex;
        flex-direction: column;
    }

    .portfolio-list li {
        border-bottom: var(--border);
    }

    .portfolio-list a {
        display: block;
        padding: 1.5rem 0;
        color: #111;
        text-decoration: none;
        font-size: 1.25rem;
        font-weight: 500;
        display: flex;
        justify-content: space-between;
        transition: color 0.2s ease;
    }

    .portfolio-list a:hover {
        color: #666;
    }

    /* Footer */
    footer {
        padding: var(--space-lg) 0 var(--space-xl);
        border-top: var(--border);
        text-align: center;
    }

    footer h3 {
        font-size: 2rem;
        margin: 0 0 1rem 0;
    }

    footer p {
        color: #666;
        margin: 0 auto var(--space-md);
        max-width: 500px;
    }
</style>
