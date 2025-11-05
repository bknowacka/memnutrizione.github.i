<!DOCTYPE html>
<html lang="it">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dieta Antigonfiore - Demo Interattiva</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Carichiamo un font carino e giocoso */
        @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap');
        
        body {
            font-family: 'Poppins', 'Inter', sans-serif;
            overflow: hidden; /* Previene lo scrolling */
        }

        /* Animazione per far fluttuare gli elementi */
        @keyframes float {
            0% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-20px) rotate(5deg); }
            100% { transform: translateY(0px) rotate(0deg); }
        }

        .food-icon {
            position: absolute;
            font-size: 3rem; /* Dimensione grande per le emoji */
            animation: float 6s ease-in-out infinite;
            opacity: 0.7;
            transition: all 0.3s ease;
            z-index: 0;
            user-select: none; /* Impedisce la selezione */
        }

        .food-icon:hover {
            opacity: 1;
            transform: scale(1.2);
            z-index: 10;
        }

        /* Effetto di "soffio" per il pulsante */
        @keyframes pulse-light {
            0% { box-shadow: 0 0 0 0 rgba(22, 163, 74, 0.7); }
            70% { box-shadow: 0 0 0 15px rgba(22, 163, 74, 0); }
            100% { box-shadow: 0 0 0 0 rgba(22, 163, 74, 0); }
        }

        .pulse-button {
            animation: pulse-light 2.5s infinite;
        }
        
        /* Animazione di entrata per la modale */
        @keyframes modal-fade-in {
            from { opacity: 0; transform: scale(0.9) translateY(20px); }
            to { opacity: 1; transform: scale(1) translateY(0); }
        }
        
        #success-modal {
            animation: modal-fade-in 0.5s cubic-bezier(0.25, 0.46, 0.45, 0.94) forwards;
        }

        /* Animazione di uscita per la card principale */
        @keyframes card-fade-out {
            from { opacity: 1; transform: scale(1); }
            to { opacity: 0; transform: scale(0.9); }
        }
        
        .card-exit {
            animation: card-fade-out 0.5s ease-out forwards;
        }
    </style>
</head>
<body class="h-screen w-screen bg-gradient-to-br from-orange-400 to-green-500">

    <!-- Contenitore principale per le icone e la card -->
    <div id="app-container" class="relative h-full w-full flex items-center justify-center p-4">

        <!-- Card Principale (Il "Test") -->
        <div id="main-card" class="relative z-10 w-full max-w-lg bg-white/90 backdrop-blur-lg rounded-3xl shadow-2xl p-8 md:p-12 text-center transition-all duration-500">
            <h1 class="text-4xl md:text-5xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-orange-500 to-green-600 mb-4">
                DIETA ANTIGONFIORE
            </h1>
            <p class="text-xl text-gray-700 mb-8">
                Fai il test online e ricevi <span class="font-bold text-green-700">GRATIS</span> la tua dieta!
            </p>
            
            <!-- Pulsante CTA (Ora è un link!) -->
            <!-- NOTA: Sostituisci IL_TUO_LINK_GOOGLE_FORM_QUI con il link reale del tuo modulo! -->
            <a id="cta-button" 
               href="IL_TUO_LINK_GOOGLE_FORM_QUI" 
               target="_blank" 
               class="pulse-button block w-full py-4 px-8 bg-green-600 text-white text-xl font-bold rounded-full shadow-lg transform transition-all duration-300 hover:bg-green-700 hover:scale-105 active:scale-95">
                INIZIA IL TEST ORA!
            </a>
            <!-- Ho rimosso il paragrafo <p id="loader"> perché non è più necessario -->
        </div>

        <!-- Schermata di Successo (Rimossa perché il link porta direttamente al form) -->
        <!-- <div id="success-modal" ... > ... </div> -->

    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const container = document.getElementById('app-container');
            const mainCard = document.getElementById('main-card');
            // Rimossi i riferimenti a ctaButton, loader, e successModal
            // perché l'interazione principale è ora un semplice link <a>.

            const foodEmojis = ['🥑', '🥬', '🫚', '🥣', '🥤', '🍓', '🫐', '🥦'];
            const numIcons = 20; // Numero di icone fluttuanti

            // 1. Creare le icone di cibo fluttuanti
            for (let i = 0; i < numIcons; i++) {
                const icon = document.createElement('div');
                icon.classList.add('food-icon');
                icon.textContent = foodEmojis[Math.floor(Math.random() * foodEmojis.length)];
                
                // Posizionamento e animazione casuali
                icon.style.top = `${Math.random() * 100}%`;
                icon.style.left = `${Math.random() * 100}%`;
                icon.style.fontSize = `${Math.random() * 2 + 2}rem`; // 2rem a 4rem
                icon.style.animationDelay = `${Math.random() * 5}s`;
                icon.style.animationDuration = `${Math.random() * 5 + 5}s`; // 5s a 10s
                
                container.appendChild(icon);
            }

            // 2. Gestire l'interazione del "Test"
            // Tutta la logica Javascript per il click, il caricamento e la modale
            // è stata rimossa perché il pulsante è ora un link <a>
            // che porta direttamente al Google Form.
        });
    </script>

</body>
</html>
