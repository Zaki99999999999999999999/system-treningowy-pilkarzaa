<!DOCTYPE html>
<html lang="pl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>System Treningowy Piłkarza</title>
    <meta name="theme-color" content="#1a2a6c">
    <link rel="manifest" href="manifest.json">
    <link rel="icon" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text y=%22.9em%22 font-size=%2290%22>⚽</text></svg>">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        :root {
            --primary: #1a2a6c;
            --secondary: #2a4a6c;
            --accent: #4a6a8c;
            --light: #f8f9fa;
            --dark: #333;
            --success: #28a745;
            --warning: #ffc107;
            --danger: #dc3545;
        }
        
        body {
            background: linear-gradient(135deg, var(--primary), var(--secondary), var(--accent));
            color: var(--dark);
            line-height: 1.6;
            padding: 20px;
            min-height: 100vh;
        }
        
        .container {
            max-width: 1400px;
            margin: 0 auto;
            background: white;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
            overflow: hidden;
        }
        
        header {
            background: linear-gradient(to right, var(--primary), var(--secondary));
            color: white;
            text-align: center;
            padding: 40px 20px;
            position: relative;
        }
        
        h1 {
            font-size: 2.8rem;
            margin-bottom: 15px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
        }
        
        .subtitle {
            font-size: 1.4rem;
            opacity: 0.9;
            margin-bottom: 10px;
        }
        
        .tagline {
            font-style: italic;
            font-size: 1.1rem;
            opacity: 0.8;
        }
        
        .content {
            padding: 30px;
        }
        
        section {
            margin-bottom: 40px;
            padding: 25px;
            border-radius: 10px;
            background: var(--light);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            transition: transform 0.3s ease;
        }
        
        section:hover {
            transform: translateY(-5px);
        }
        
        h2 {
            color: var(--primary);
            border-bottom: 2px solid var(--secondary);
            padding-bottom: 10px;
            margin-bottom: 20px;
            font-size: 1.8rem;
            display: flex;
            align-items: center;
        }
        
        h2::before {
            content: '';
            display: inline-block;
            width: 10px;
            height: 30px;
            background: var(--secondary);
            margin-right: 15px;
            border-radius: 5px;
        }
        
        h3 {
            color: var(--secondary);
            margin: 15px 0 10px;
            font-size: 1.4rem;
        }
        
        /* Reszta stylów pozostaje taka sama jak w poprzednim kodzie */
        /* ... (wklej tutaj wszystkie style z poprzedniego kodu) ... */
        
        .install-btn {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: var(--success);
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 50px;
            cursor: pointer;
            font-weight: bold;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
            z-index: 1000;
            display: none;
        }
        
        @media (max-width: 768px) {
            .install-btn {
                bottom: 10px;
                right: 10px;
                padding: 10px 15px;
                font-size: 0.9rem;
            }
        }
    </style>
</head>
<body>
    <button class="install-btn" id="installButton">Zainstaluj App</button>
    
    <div class="container">
        <header>
            <h1>⚽ Kompletny System Treningowy Piłkarza</h1>
            <p class="subtitle">Ultimate Edition v8.0 - Pełna Integracja</p>
            <p class="tagline">Od planu treningowego po rozwój mentalny - wszystko w jednym miejscu</p>
        </header>
        
        <div class="content">
            <!-- Tutaj wklej całą zawartość z poprzedniego kodu -->
            <!-- ASYSTENT AI -->
            <section>
                <h2>🤖 Asystent AI - Dostosuj Swój Plan</h2>
                <div class="ai-assistant">
                    <!-- Zawartość asystenta AI -->
                </div>
            </section>

            <!-- KALENDARZE -->
            <section class="calendar-section">
                <h2>📅 Kalendarze - Zarządzaj Swoim Czasem</h2>
                <!-- Zawartość kalendarzy -->
            </section>

            <!-- ... i tak dalej dla wszystkich sekcji ... -->
        </div>
        
        <footer>
            <p>© 2023 Kompletny System Treningowy Piłkarza | Ultimate Complete Edition</p>
            <p style="margin-top: 10px; font-size: 0.9rem; opacity: 0.8;">Twoja droga do mistrzostwa zaczyna się tutaj. Działaj!</p>
        </footer>
    </div>

    <script>
        // Service Worker Registration dla PWA
        if ('serviceWorker' in navigator) {
            window.addEventListener('load', function() {
                navigator.serviceWorker.register('./sw.js')
                    .then(function(registration) {
                        console.log('Service Worker zarejestrowany pomyślnie:', registration);
                    })
                    .catch(function(error) {
                        console.log('Rejestracja Service Worker nie powiodła się:', error);
                    });
            });
        }

        // Instalacja PWA
        let deferredPrompt;
        const installButton = document.getElementById('installButton');

        window.addEventListener('beforeinstallprompt', (e) => {
            e.preventDefault();
            deferredPrompt = e;
            installButton.style.display = 'block';
        });

        installButton.addEventListener('click', async () => {
            if (deferredPrompt) {
                deferredPrompt.prompt();
                const { outcome } = await deferredPrompt.userChoice;
                if (outcome === 'accepted') {
                    installButton.style.display = 'none';
                }
                deferredPrompt = null;
            }
        });

        window.addEventListener('appinstalled', () => {
            installButton.style.display = 'none';
            deferredPrompt = null;
        });

        // Tutaj wklej cały JavaScript z poprzedniego kodu
        // ... (wklej tutaj cały kod JavaScript z poprzedniej odpowiedzi) ...
    </script>
</body>
</html>
