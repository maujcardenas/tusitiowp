<script>
    const paquetes = [
        {
            id: "wp-init",
            nombre: "Plan Instalación WP",
            enfoque:
                "Para quienes deseen libertad de diseñar con sistema WordPress",
            precio: "$108",
            detallesPrecio: "renovables cada año",
            caracteristicas: [
                "1 Dominio + Hosting 6Gb",
                "3 correos empresariales (1Gb c/u)",
                "Instalación limpia de WP totalmente actualizado",
                "Autonomía total de edición",
            ],
            destacado: false,
        },
        {
            id: "pro",
            nombre: "Plan Profesional",
            enfoque:
                "Para mostrar servicios (profesionales, artísticos, academias, etc.)",
            precio: "$288",
            detallesPrecio: "$108 renovable/año + $180 una sola vez",
            caracteristicas: [
                "1 Dominio + Hosting 6Gb",
                "3 correos empresariales (1Gb c/u)",
                "Sitio web a medida (5-10 secciones)",
                "Formularios de contacto, redes sociales y blog",
            ],
            destacado: true, // Este plan se llevará la atención visual
        },
        {
            id: "ecommerce",
            nombre: "Plan E-Commerce",
            enfoque:
                "Para marcas que buscan vender múltiples productos o servicios en línea",
            precio: "$468",
            detallesPrecio: "$108/anual + $360 una sola vez",
            caracteristicas: [
                "1 Dominio + Hosting 6Gb",
                "3 correos empresariales (1Gb c/u)",
                "Sitio web optimizado (5-10 secciones)",
                "Módulo completo de E-commerce",
            ],
            destacado: false,
        },
    ];
</script>

<section class="packages-section">
    <div class="header-meta">
        <span class="tag">Precios transparentes</span>
        <h2>Planes Diseñados a tu Medida</h2>
    </div>

    <div class="packages-grid">
        {#each paquetes as paquete}
            <article class="package-card" class:featured={paquete.destacado}>
                {#if paquete.destacado}
                    <span class="badge">Recomendado</span>
                {/if}

                <div class="card-header">
                    <h3>{paquete.nombre}</h3>
                    <p class="enfoque">{paquete.enfoque}</p>
                </div>

                <div class="price-block">
                    <div class="main-price">
                        <strong>{paquete.precio}</strong>
                    </div>
                    <p class="price-legend">{paquete.detallesPrecio}</p>
                </div>

                <ul class="specs-list">
                    {#each paquete.caracteristicas as item}
                        <li>{item}</li>
                    {/each}
                </ul>

                <div class="action-footer">
                    <a href="#contacto" class="btn-select">
                        {paquete.destacado
                            ? "Iniciar Proyecto Pro"
                            : "Seleccionar Plan"}
                    </a>
                </div>
            </article>
        {/each}
    </div>
</section>

<style>
    /* Contenedor y sección general */
    .packages-section {
        padding: var(--space-xl, 6rem) 0;
        background-color: #fafafa;
    }

    .header-meta {
        text-align: center;
        margin-bottom: var(--space-lg, 4rem);
    }

    .header-meta .tag {
        font-size: 0.85rem;
        text-transform: uppercase;
        letter-spacing: 0.15em;
        color: #888;
        font-weight: 600;
    }

    .header-meta h2 {
        font-size: clamp(2rem, 5vw, 3rem);
        font-weight: 700;
        letter-spacing: -0.03em;
        margin: 0.5rem 0 0 0;
        color: #111;
    }

    /* Grid altamente adaptable sin Media Queries */
    .packages-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(min(100%, 320px), 1fr));
        gap: 2.5rem;
        align-items: stretch;
    }

    /* Estructura minimalista de las tarjetas */
    .package-card {
        background: #ffffff;
        border: 1px solid #eaeaea;
        border-radius: 12px;
        padding: 3rem 2.25rem 2.25rem 2.25rem;
        display: flex;
        flex-direction: column;
        position: relative;
        transition:
            transform 0.3s cubic-bezier(0.16, 1, 0.3, 1),
            border-color 0.3s ease;
    }

    .package-card:hover {
        transform: translateY(-4px);
        border-color: #b5b5b5;
    }

    /* Tratamiento sutil pero prominente para el plan destacado */
    .package-card.featured {
        border: 2px solid #111111;
        box-shadow: 0 20px 40px rgba(0, 0, 0, 0.04);
    }

    .badge {
        position: absolute;
        top: -14px;
        left: 2.25rem;
        background: #111111;
        color: #ffffff;
        font-size: 0.75rem;
        font-weight: 600;
        text-transform: uppercase;
        letter-spacing: 0.08em;
        padding: 0.35rem 1rem;
        border-radius: 50px;
    }

    /* Elementos internos */
    .card-header h3 {
        font-size: 1.5rem;
        font-weight: 600;
        margin: 0 0 0.75rem 0;
        color: #111;
    }

    .enfoque {
        color: #666;
        min-height: 2.85rem; /* Mantiene la alineación visual entre tarjetas */
    }

    /* Bloque de precios */
    .price-block {
        margin: 2.5rem 0;
        padding-bottom: 1.5rem;
        border-style: dotted;
        border-color: #666;
        border-width: 1px 0px 1px 0px;
        padding: 1rem 0rem 1rem 0rem;
    }

    .main-price {
        display: flex;
        align-items: baseline;
        gap: 0.25rem;
        color: #111;
        font-size: 2.5rem;
        font-weight: 700;
        letter-spacing: -0.02em;
        line-height: 1;
    }

    .price-legend {
        font-size: 0.85rem;
        color: #888;
        margin: 0.5rem 0 0 0;
    }

    /* Características técnicas */
    .specs-list {
        list-style: none;
        padding: 0;
        margin: 0 0 3rem 0;
        display: flex;
        flex-direction: column;
        gap: 1rem;
        flex-grow: 1; /* Empuja el botón hacia abajo para alinearlos */
    }

    .specs-list li {
        font-size: 0.95rem;
        color: #444;
        position: relative;
        padding-left: 1.25rem;
        line-height: 1.4;
    }

    /* Viñeta minimalista (un guión limpio o punto) */
    .specs-list li::before {
        content: "—";
        position: absolute;
        left: 0;
        color: #999;
    }

    /* Botón de acción */
    .action-footer {
        width: 100%;
    }

    .btn-select {
        display: block;
        text-align: center;
        background: transparent;
        color: #111;
        border: 1px solid #111;
        text-decoration: none;
        padding: 1rem;
        border-radius: 6px;
        font-weight: 500;
        font-size: 0.95rem;
        transition:
            background 0.2s ease,
            color 0.2s ease;
    }

    .package-card.featured .btn-select {
        background: #111111;
        color: #ffffff;
    }

    .btn-select:hover {
        background: #111111;
        color: #ffffff;
    }

    .package-card.featured .btn-select:hover {
        background: #333333;
        border-color: #333333;
    }
</style>
