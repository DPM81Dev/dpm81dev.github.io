<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DPM81Dev v.1</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --bg-primary: #fafafa;
            --bg-secondary: #ffffff;
            --text-primary: #2c2c2c;
            --text-secondary: #6b6b6b;
            --accent: #7a9eb5;
            --border: #e5e5e5;
            --shadow: rgba(0, 0, 0, 0.05);
        }

        [data-theme="dark"] {
            --bg-primary: #1a1a1a;
            --bg-secondary: #242424;
            --text-primary: #e8e8e8;
            --text-secondary: #a8a8a8;
            --accent: #8ba9c0;
            --border: #3a3a3a;
            --shadow: rgba(0, 0, 0, 0.3);
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
            background-color: var(--bg-primary);
            color: var(--text-primary);
            line-height: 1.6;
            transition: background-color 0.3s ease, color 0.3s ease;
        }

        header {
            background-color: var(--bg-secondary);
            border-bottom: 1px solid var(--border);
            padding: 1rem 0;
            position: sticky;
            top: 0;
            z-index: 100;
            box-shadow: 0 2px 8px var(--shadow);
        }

        nav {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--accent);
            letter-spacing: 1px;
            font-family: 'Courier New', monospace;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
            list-style: none;
        }

        .nav-links a {
            color: var(--text-secondary);
            text-decoration: none;
            transition: color 0.3s ease;
            font-weight: 500;
        }

        .nav-links a:hover {
            color: var(--accent);
        }

        .theme-toggle {
            background: none;
            border: 1px solid var(--border);
            color: var(--text-primary);
            padding: 0.5rem 1rem;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-size: 0.9rem;
        }

        .theme-toggle:hover {
            background-color: var(--accent);
            color: white;
            border-color: var(--accent);
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        section {
            padding: 4rem 0;
            min-height: 70vh;
        }

        h1 {
            font-size: 3rem;
            margin-bottom: 1rem;
            color: var(--text-primary);
        }

        h2 {
            font-size: 2rem;
            margin-bottom: 2rem;
            color: var(--accent);
            border-bottom: 2px solid var(--border);
            padding-bottom: 0.5rem;
        }

        .typewriter {
            overflow: hidden;
            border-right: 3px solid var(--accent);
            white-space: nowrap;
            animation: typing 3s steps(30, end), blink-caret 0.75s step-end infinite;
            display: inline-block;
        }

        @keyframes typing {
            from { width: 0 }
            to { width: 100% }
        }

        @keyframes blink-caret {
            from, to { border-color: transparent }
            50% { border-color: var(--accent) }
        }

        h3 {
            font-size: 1.3rem;
            margin-bottom: 0.5rem;
            color: var(--text-primary);
        }

        .hero {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 80vh;
        }

        .hero-content {
            display: flex;
            flex-direction: column;
            align-items: flex-start;
            max-width: 1200px;
            padding: 0 2rem;
        }

        .hero-text {
            text-align: left;
        }

        .hero p {
            font-size: 1.3rem;
            color: var(--text-secondary);
            margin-bottom: 2rem;
            max-width: 600px;
        }

        .social-links {
            display: flex;
            gap: 1.5rem;
            margin-top: 2rem;
        }

        .social-link {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background-color: var(--bg-secondary);
            border: 2px solid var(--border);
            color: var(--text-primary);
            text-decoration: none;
            font-size: 1.5rem;
            transition: all 0.3s ease;
        }

        .social-link:hover {
            background-color: var(--accent);
            color: white;
            border-color: var(--accent);
            transform: translateY(-3px);
        }

        .card {
            background-color: var(--bg-secondary);
            border: 1px solid var(--border);
            border-radius: 8px;
            padding: 2rem;
            margin-bottom: 2rem;
            box-shadow: 0 2px 8px var(--shadow);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .card:hover {
            transform: translateY(-4px);
            box-shadow: 0 4px 16px var(--shadow);
        }

        .cv-section {
            margin-bottom: 2rem;
        }

        .cv-item {
            margin-bottom: 1.5rem;
        }

        .cv-item h4 {
            color: var(--text-primary);
            margin-bottom: 0.3rem;
        }

        .cv-item .date {
            color: var(--accent);
            font-size: 0.9rem;
            font-weight: 500;
        }

        .cv-item p {
            color: var(--text-secondary);
            margin-top: 0.5rem;
        }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .project-card {
            background-color: var(--bg-secondary);
            border: 1px solid var(--border);
            border-radius: 8px;
            padding: 2rem;
            box-shadow: 0 2px 8px var(--shadow);
        }

        .project-url {
            color: var(--accent);
            text-decoration: none;
            font-size: 0.9rem;
            margin-bottom: 1rem;
            display: inline-block;
        }

        .project-url:hover {
            text-decoration: underline;
        }

        .project-description {
            color: var(--text-secondary);
            margin-bottom: 1rem;
            line-height: 1.6;
        }

        .screenshots-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 0.5rem;
            margin-top: 1rem;
        }

        .screenshot-card {
            background-color: var(--bg-primary);
            border: 1px solid var(--border);
            border-radius: 4px;
            height: 100px;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }

        .screenshot-card img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .screenshot-placeholder {
            color: var(--text-secondary);
            font-size: 0.8rem;
        }

        .project-tag {
            display: inline-block;
            background-color: var(--accent);
            color: white;
            padding: 0.3rem 0.8rem;
            border-radius: 15px;
            font-size: 0.85rem;
            margin-right: 0.5rem;
            margin-top: 0.5rem;
        }

        .contact-form {
            max-width: 600px;
            margin: 0 auto;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        label {
            display: block;
            margin-bottom: 0.5rem;
            color: var(--text-primary);
            font-weight: 500;
        }

        input, textarea {
            width: 100%;
            padding: 0.8rem;
            border: 1px solid var(--border);
            border-radius: 4px;
            background-color: var(--bg-secondary);
            color: var(--text-primary);
            font-family: inherit;
            transition: border-color 0.3s ease;
        }

        input:focus, textarea:focus {
            outline: none;
            border-color: var(--accent);
        }

        textarea {
            resize: vertical;
            min-height: 150px;
        }

        button[type="submit"] {
            background-color: var(--accent);
            color: white;
            padding: 0.8rem 2rem;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 1rem;
            font-weight: 500;
            transition: opacity 0.3s ease;
        }

        button[type="submit"]:hover {
            opacity: 0.9;
        }

        footer {
            background-color: var(--bg-secondary);
            border-top: 1px solid var(--border);
            padding: 2rem 0;
            text-align: center;
            color: var(--text-secondary);
        }

        @media (max-width: 768px) {
            h1 {
                font-size: 2rem;
            }

            h2 {
                font-size: 1.5rem;
            }

            .nav-links {
                gap: 1rem;
            }

            section {
                padding: 3rem 0;
            }

            .projects-grid {
                grid-template-columns: 1fr;
            }

            .hero-content {
                flex-direction: column;
                text-align: left;
            }

            .hero-text {
                text-align: left;
            }

            .profile-pic {
                width: 200px;
                height: 200px;
            }

            .social-links {
                justify-content: center;
            }
        }
    </style>
</head>
<body>
    <header>
        <nav>
            <div class="logo"></div>
            <ul class="nav-links">
                <li><a href="#quien-soy">¿Quién soy?</a></li>
                <li><a href="#curriculum">Curriculum</a></li>
                <li><a href="#proyectos">Proyectos</a></li>
                <li><a href="#contacto">Contacto</a></li>
            </ul>
            <button class="theme-toggle" onclick="toggleTheme()">🌓 Tema</button>
        </nav>
    </header>

    <main>
        <section id="quien-soy" class="hero">
            <div class="hero-content">
                <div class="hero-text">
                    <h1><span class="typewriter">Hola, soy David Pantoja Malfeito</span></h1>
                    <p>Profesional dedicado con pasión por la tecnología y la innovación. Especializado en crear soluciones que marcan la diferencia.</p>
                    <div class="social-links">
                        <a href="https://github.com/tu-usuario" target="_blank" class="social-link" title="GitHub">
                            <svg width="24" height="24" fill="currentColor" viewBox="0 0 24 24">
                                <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
                            </svg>
                        </a>
                        <a href="https://linkedin.com/in/tu-usuario" target="_blank" class="social-link" title="LinkedIn">
                            <svg width="24" height="24" fill="currentColor" viewBox="0 0 24 24">
                                <path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/>
                            </svg>
                        </a>
                        <a href="#" onclick="downloadCV(event)" class="social-link" title="Descargar CV">
                            <svg width="24" height="24" fill="currentColor" viewBox="0 0 24 24">
                                <path d="M11.363 2c4.155 0 2.637 6 2.637 6s6-1.65 6 2.457v11.543h-16v-20h7.363zm.826-2h-10.189v24h20v-14.386c0-2.391-6.648-9.614-9.811-9.614zm4.811 13h-2.628v3.686h.907v-1.472h1.49v-.732h-1.49v-.698h1.721v-.784zm-4.9 0h-1.599v3.686h1.599c.537 0 .961-.181 1.262-.535.555-.658.587-2.034-.062-2.692-.298-.3-.712-.459-1.2-.459zm-.692.783h.496c.473 0 .802.173.915.644.064.267.077.679-.021.948-.128.351-.381.528-.754.528h-.637v-2.12zm-2.74-.783h-1.668v3.686h.907v-1.277h.761c.619 0 1.064-.277 1.224-.763.095-.291.095-.597 0-.885-.16-.484-.606-.761-1.224-.761zm-.761.732h.546c.235 0 .467.028.576.228.067.123.067.366 0 .489-.109.199-.341.227-.576.227h-.546v-.944z"/>
                            </svg>
                        </a>
                    </div>
                </div>
            </div>
        </section>

        <section id="curriculum">
            <div class="container">
                <h2>Curriculum Vitae</h2>
                
                <div class="card cv-section">
                    <h3>Experiencia Profesional</h3>
                    <div class="cv-item">
                        <h4>Puesto de Trabajo</h4>
                        <p class="date">Enero 2023 - Actualidad</p>
                        <p>Descripción de las responsabilidades y logros principales en este puesto.</p>
                    </div>
                    <div class="cv-item">
                        <h4>Puesto Anterior</h4>
                        <p class="date">Marzo 2021 - Diciembre 2022</p>
                        <p>Descripción de las responsabilidades y logros en el puesto anterior.</p>
                    </div>
                </div>

                <div class="card cv-section">
                    <h3>Formación Académica</h3>
                    <div class="cv-item">
                        <h4>Título Universitario</h4>
                        <p class="date">2017 - 2021</p>
                        <p>Universidad o institución educativa</p>
                    </div>
                </div>

                <div class="card cv-section">
                    <h3>Habilidades</h3>
                    <p>• Programación y desarrollo web<br>
                    • Gestión de proyectos<br>
                    • Comunicación efectiva<br>
                    • Trabajo en equipo<br>
                    • Resolución de problemas</p>
                </div>
            </div>
        </section>

        <section id="proyectos">
            <div class="container">
                <h2>Proyectos</h2>
                <div class="projects-grid">
                    <div class="project-card">
                        <h3>Proyecto 1</h3>
                        <a href="https://ejemplo.com/proyecto1" target="_blank" class="project-url">🔗 Ver proyecto</a>
                        <p class="project-description">Descripción breve del proyecto y los objetivos que se alcanzaron con su implementación.</p>
                        <div>
                            <span class="project-tag">Web</span>
                            <span class="project-tag">JavaScript</span>
                        </div>
                        <div class="screenshots-grid">
                            <div class="screenshot-card">
                                <span class="screenshot-placeholder">Screenshot 1</span>
                            </div>
                            <div class="screenshot-card">
                                <span class="screenshot-placeholder">Screenshot 2</span>
                            </div>
                            <div class="screenshot-card">
                                <span class="screenshot-placeholder">Screenshot 3</span>
                            </div>
                            <div class="screenshot-card">
                                <span class="screenshot-placeholder">Screenshot 4</span>
                            </div>
                        </div>
                    </div>
                    <div class="project-card">
                        <h3>Proyecto 2</h3>
                        <a href="https://ejemplo.com/proyecto2" target="_blank" class="project-url">🔗 Ver proyecto</a>
                        <p class="project-description">Descripción del segundo proyecto destacado con sus características principales.</p>
                        <div>
                            <span class="project-tag">Diseño</span>
                            <span class="project-tag">UX/UI</span>
                        </div>
                        <div class="screenshots-grid">
                            <div class="screenshot-card">
                                <span class="screenshot-placeholder">Screenshot 1</span>
                            </div>
                            <div class="screenshot-card">
                                <span class="screenshot-placeholder">Screenshot 2</span>
                            </div>
                            <div class="screenshot-card">
                                <span class="screenshot-placeholder">Screenshot 3</span>
                            </div>
                            <div class="screenshot-card">
                                <span class="screenshot-placeholder">Screenshot 4</span>
                            </div>
                        </div>
                    </div>
                    <div class="project-card">
                        <h3>Proyecto 3</h3>
                        <a href="https://ejemplo.com/proyecto3" target="_blank" class="project-url">🔗 Ver proyecto</a>
                        <p class="project-description">Otro proyecto importante que muestra tus habilidades y experiencia profesional.</p>
                        <div>
                            <span class="project-tag">Desarrollo</span>
                            <span class="project-tag">API</span>
                        </div>
                        <div class="screenshots-grid">
                            <div class="screenshot-card">
                                <span class="screenshot-placeholder">Screenshot 1</span>
                            </div>
                            <div class="screenshot-card">
                                <span class="screenshot-placeholder">Screenshot 2</span>
                            </div>
                            <div class="screenshot-card">
                                <span class="screenshot-placeholder">Screenshot 3</span>
                            </div>
                            <div class="screenshot-card">
                                <span class="screenshot-placeholder">Screenshot 4</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section id="contacto">
            <div class="container">
                <h2>Contacto</h2>
                <form class="contact-form" onsubmit="handleSubmit(event)">
                    <div class="form-group">
                        <label for="nombre">Nombre</label>
                        <input type="text" id="nombre" name="nombre" required>
                    </div>
                    <div class="form-group">
                        <label for="email">Email</label>
                        <input type="email" id="email" name="email" required>
                    </div>
                    <div class="form-group">
                        <label for="mensaje">Mensaje</label>
                        <textarea id="mensaje" name="mensaje" required></textarea>
                    </div>
                    <button type="submit">Enviar Mensaje</button>
                </form>
            </div>
        </section>
    </main>

    <footer>
        <div class="container">
            <p>&copy; 2025 [Tu Nombre]. Todos los derechos reservados.</p>
        </div>
    </footer>

    <script>
        function toggleTheme() {
            const html = document.documentElement;
            const currentTheme = html.getAttribute('data-theme');
            const newTheme = currentTheme === 'dark' ? 'light' : 'dark';
            html.setAttribute('data-theme', newTheme);
        }

        function downloadCV(event) {
            event.preventDefault();
            // Aquí debes colocar la URL de tu archivo PDF
            // Ejemplo: window.location.href = 'ruta/a/tu/curriculum.pdf';
            alert('Por favor, actualiza la función downloadCV() con la ruta de tu archivo PDF');
        }

        function handleSubmit(event) {
            event.preventDefault();
            alert('¡Gracias por tu mensaje! Me pondré en contacto contigo pronto.');
            event.target.reset();
        }

        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                target.scrollIntoView({
                    behavior: 'smooth',
                    block: 'start'
                });
            });
        });
    </script>
</body>
</html>
