# Gmsftse
FTSE 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
    <title>Gamer Money Studios - Finish the Story Engine</title>
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Rajdhani:wght@700&family=Cutive+Mono&display=swap" rel="stylesheet">

    <style>
        :root {
            --primary-font: 'Rajdhani', sans-serif;
            --screenplay-font: 'Cutive Mono', monospace;
            --text-color: #FFFFFF;
            --background-color: #000000;
            --red-accent: #FF0000;
            --blue-accent: #00A8FF;
            --current-accent: var(--red-accent);
        }
        body {
            font-family: var(--primary-font);
            color: var(--text-color);
            background-color: var(--background-color);
            -webkit-font-smoothing: antialiased;
        }
        .screenplay-text-font { font-family: var(--screenplay-font); }
        @keyframes fadeIn { to { opacity: 1; } }
        @keyframes pulse { 0%, 100% { transform: scale(1); opacity: 0.9; } 50% { transform: scale(1.05); opacity: 1; } }
        @keyframes blink { 50% { opacity: 0; } }
        .animate-fade-in { animation: fadeIn 1s forwards; }
        .animate-pulse { animation: pulse 2.5s infinite ease-in-out; }
        .typing-cursor {
            display: inline-block;
            background-color: var(--current-accent);
            width: 10px;
            height: 1.4em;
            animation: blink 1s step-end infinite;
            vertical-align: text-bottom;
            margin-left: 2px;
            box-shadow: 0 0 10px var(--current-accent);
        }
        .ip-video-bg {
            position: absolute; top: 50%; left: 50%;
            width: 177.77vh; height: 100vh;
            min-width: 100%; min-height: 56.25vw;
            transform: translate(-50%, -50%);
            z-index: 1;
        }
        .meter-blue { background-color: var(--blue-accent); }
        .meter-red { background-color: var(--red-accent); }
    </style>
</head>
<body class="bg-black text-white m-0 p-0 w-full h-screen overflow-hidden">

    <!-- Splash Screen -->
    <div id="splash-screen" class="screen w-full h-full flex flex-col justify-center items-center opacity-0 animate-fade-in">
        <svg class="w-3/5 max-w-[250px] animate-pulse" viewBox="0 0 200 100" xmlns="http://www.w3.org/2000/svg">
            <defs>
                <linearGradient id="grad1" x1="0%" y1="0%" x2="100%" y2="0%">
                    <stop offset="0%" style="stop-color:var(--blue-accent);stop-opacity:1" />
                    <stop offset="100%" style="stop-color:var(--red-accent);stop-opacity:1" />
                </linearGradient>
            </defs>
            <text x="50%" y="50%" dominant-baseline="middle" text-anchor="middle" font-family="Rajdhani, sans-serif" font-size="60" font-weight="bold" fill="url(#grad1)">GMS</text>
            <text x="50%" y="75%" dominant-baseline="middle" text-anchor="middle" font-family="Rajdhani, sans-serif" font-size="14" fill="#888">FINISH THE STORY ENGINE</text>
        </svg>
    </div>

    <!-- Hub Screen (Story Selection with Live Canon Meters) -->
    <div id="hub-screen" class="screen hidden w-full h-full flex flex-col justify-center items-center p-5 box-border opacity-0">
        <h1 class="text-3xl font-bold text-center mb-5" style="color: var(--red-accent); text-shadow: 0 0 10px rgba(255,0,0,0.5);">CHOOSE YOUR STORY</h1>
        <div class="flex flex-col w-full max-w-2xl h-auto space-y-6">
            <!-- Bear by Blade Panel -->
            <div class="flex flex-col">
                <div class="ip-panel h-40 border-2 border-[#333] rounded-lg relative overflow-hidden flex justify-center items-center cursor-pointer transition-all duration-200 ease-in-out hover:border-[var(--red-accent)] hover:shadow-[0_0_20px_var(--red-accent)] active:scale-95" data-ip="bear_by_blade">
                    <iframe class="ip-video-bg" src="https://www.youtube.com/embed/zwqVnrFnLO8?autoplay=1&mute=1&loop=1&playlist=zwqVnrFnLO8&controls=0&showinfo=0&autohide=1&modestbranding=1" frameborder="0" allow="autoplay"></iframe>
                    <h2 class="text-4xl font-bold z-10 bg-black bg-opacity-60 px-4 py-2 rounded">BEAR BY BLADE</h2>
                </div>
                <div class="mt-2 text-center">
                    <p class="text-sm text-gray-400">GLOBAL CANON</p>
                    <div class="w-full h-2 bg-[#111] border border-[#444] rounded-full mt-1 flex overflow-hidden">
                        <div id="canon-meter-blue-bear_by_blade" class="h-full meter-blue transition-all duration-500"></div>
                        <div id="canon-meter-red-bear_by_blade" class="h-full meter-red transition-all duration-500"></div>
                    </div>
                    <p id="canon-text-bear_by_blade" class="text-xs text-gray-300 mt-1">Calculating...</p>
                </div>
            </div>
            <!-- Project Invictus Panel -->
            <div class="flex flex-col">
                <div class="ip-panel h-40 border-2 border-[#333] rounded-lg relative overflow-hidden flex justify-center items-center cursor-pointer transition-all duration-200 ease-in-out hover:border-[var(--blue-accent)] hover:shadow-[0_0_20px_var(--blue-accent)] active:scale-95" data-ip="project_invictus">
                    <iframe class="ip-video-bg" src="https://www.youtube.com/embed/0uoaZZRbwqg?autoplay=1&mute=1&loop=1&playlist=0uoaZZRbwqg&controls=0&showinfo=0&autohide=1&modestbranding=1" frameborder="0" allow="autoplay"></iframe>
                    <h2 class="text-4xl font-bold z-10 bg-black bg-opacity-60 px-4 py-2 rounded">PROJECT INVICTUS</h2>
                </div>
                 <div class="mt-2 text-center">
                    <p class="text-sm text-gray-400">GLOBAL CANON</p>
                    <div class="w-full h-2 bg-[#111] border border-[#444] rounded-full mt-1 flex overflow-hidden">
                        <div id="canon-meter-blue-project_invictus" class="h-full meter-blue transition-all duration-500"></div>
                        <div id="canon-meter-red-project_invictus" class="h-full meter-red transition-all duration-500"></div>
                    </div>
                    <p id="canon-text-project_invictus" class="text-xs text-gray-300 mt-1">Calculating...</p>
                </div>
            </div>
        </div>
    </div>

    <!-- Demo Screen (Gameplay) -->
    <div id="demo-screen" class="screen hidden w-full h-full bg-black">
        <div id="youtube-player" class="youtube-background fixed top-[-10%] left-[-10%] w-[120%] h-[120%] pointer-events-none z-[-1] opacity-0 transition-opacity duration-1000 ease-in-out"></div>
        <div class="overlay w-full h-full bg-gradient-to-t from-black via-black/80 to-black/60 flex flex-col justify-end box-border p-4 pb-[calc(1rem+env(safe-area-inset-bottom))]">
            <a href="#" id="back-button" class="absolute top-[calc(1rem+env(safe-area-inset-top))] left-4 bg-black/50 rounded-full w-10 h-10 flex items-center justify-center z-20 text-white text-2xl no-underline">←</a>
            <div class="alignment-meter-container w-2/5 max-w-xs h-2 bg-[#222] rounded-full overflow-hidden absolute top-[calc(1.5rem+env(safe-area-inset-top))] right-4 border border-[#444] z-20">
                <div id="alignment-meter-fill" class="h-full w-1/2 transition-all duration-1000 ease-in-out"></div>
            </div>
            <div class="screenplay-container flex-grow overflow-y-auto mb-5 bg-black/30 rounded-lg p-4 border border-white/10">
                <div id="scene-header" class="text-sm opacity-70 mb-4" style="color: var(--current-accent);"></div>
                <p id="screenplay-text" class="screenplay-text-font text-lg leading-relaxed whitespace-pre-wrap" style="text-shadow: 0 0 5px var(--current-accent);"></p>
            </div>
            <div id="choice-container" class="min-h-[100px] flex flex-col justify-center border-t border-[var(--current-accent)] pt-4 space-y-3"></div>
        </div>
    </div>

    <!-- Impact Screen (Choice Consequence) -->
    <div id="impact-screen" class="screen modal-screen hidden w-full h-full flex flex-col justify-center items-center bg-black/90 p-5 text-center opacity-0">
        <h2 class="text-2xl font-bold mb-4" style="color: var(--current-accent); text-shadow: 0 0 10px var(--current-accent);">NARRATIVE SHIFT DETECTED</h2>
        <p class="text-lg">Your Choice:</p>
        <p id="impact-choice-text" class="text-lg bg-[#222] p-3 rounded-md my-3 w-full max-w-md"></p>
        <div class="alignment-meter-container w-4/5 max-w-md h-2 bg-[#222] rounded-full overflow-hidden my-5 border border-[#444]">
            <div id="impact-meter-fill" class="h-full transition-all duration-1000 ease-in-out"></div>
        </div>
        <p id="impact-consequence-text" class="text-base leading-relaxed mb-5 w-full max-w-md"></p>
        <p class="text-sm text-gray-400 tracking-widest animate-pulse">LOADING NEXT NARRATIVE BRANCH...</p>
    </div>

    <!-- Forecast Screen (End) -->
    <div id="forecast-screen" class="screen modal-screen hidden w-full h-full flex flex-col justify-center items-center bg-black/90 p-5 text-center opacity-0">
        <h2 class="text-2xl font-bold mb-4" style="color: var(--current-accent); text-shadow: 0 0 10px var(--current-accent);">CANON FORECAST</h2>
        <div class="w-full max-w-lg space-y-4">
            <div>
                <p class="text-sm text-gray-300">YOUR FINAL ALIGNMENT</p>
                <div class="forecast-meter-container w-full h-5 bg-[#111] rounded-lg overflow-hidden mt-1 border border-[#555] flex">
                    <div id="forecast-meter-blue-player" class="h-full transition-all duration-1000 ease-in-out meter-blue"></div>
                    <div id="forecast-meter-red-player" class="h-full transition-all duration-1000 ease-in-out meter-red"></div>
                </div>
            </div>
            <div>
                <p class="text-sm text-gray-300">LIVE GLOBAL CANON</p>
                <div class="forecast-meter-container w-full h-5 bg-[#111] rounded-lg overflow-hidden mt-1 border border-[#555] flex">
                    <div id="forecast-meter-blue-canon" class="h-full transition-all duration-1000 ease-in-out meter-blue"></div>
                    <div id="forecast-meter-red-canon" class="h-full transition-all duration-1000 ease-in-out meter-red"></div>
                </div>
            </div>
        </div>
        <p id="forecast-text" class="text-base leading-relaxed my-4 w-full max-w-lg"></p>
        <p class="text-xs text-gray-400 mb-6 w-full max-w-lg">Your playthrough has been recorded, influencing the live canon that will shape the cinematic sequel.</p>
        <button id="restart-button" class="choice-button w-full max-w-md py-4 rounded-lg text-base font-bold border-2 transition-colors duration-200">RETURN TO HUB</button>
    </div>

    <!-- Firebase and App Logic -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { getAuth, signInAnonymously, signInWithCustomToken, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { getFirestore, doc, runTransaction, onSnapshot, serverTimestamp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // --- 1. DEFINE ALL VARIABLES AND CONSTANTS ---

        let db, auth, userId;
        let player, currentIP, typeInterval, worldAlignment;
        let canonUnsubscribe = {}; 

        const root = document.documentElement;
        const screens = {
            splash: document.getElementById('splash-screen'),
            hub: document.getElementById('hub-screen'),
            demo: document.getElementById('demo-screen'),
            impact: document.getElementById('impact-screen'),
            forecast: document.getElementById('forecast-screen')
        };
        const choiceContainer = document.getElementById('choice-container');
        const backButton = document.getElementById('back-button');
        const restartButton = document.getElementById('restart-button');
        const alignmentFill = document.getElementById('alignment-meter-fill');
        const impactMeterFill = document.getElementById('impact-meter-fill');
        const youtubePlayerEl = document.getElementById('youtube-player');

        const storyDatabase = {
            bear_by_blade: {
                color: 'var(--red-accent)',
                start: { youtubeId: 'zwqVnrFnLO8', text: "Leo, an ambitious lion, discovers an iPhone in ancient ruins...", choices: [ { text: "Heed the Elders' warnings.", nextScene: 'elders', impactText: "You have chosen tradition over ambition...", alignmentShift: 15 }, { text: "Seize the Cube's power.", nextScene: 'power', impactText: "You have embraced forbidden technology...", alignmentShift: -15 }, ] },
                elders: { youtubeId: 'c5B8RSEUocY', text: "Leo attempts diplomacy, but his ambition gnaws at him...", choices: [ { text: "Share the power for defense.", nextScene: 'fall_of_bear_clan', impactText: "A noble choice. You use the power to protect...", alignmentShift: 20 }, { text: "Forge weapons for conquest.", nextScene: 'power', impactText: "Patience has worn thin. You build an arsenal...", alignmentShift: -20 }, ] },
                power: { youtubeId: 'V-KOaQF_qQk', text: "Consumed by his vision, Leo forges energy swords...", choices: [ { text: "Rule with a benevolent hand.", nextScene: 'elders', impactText: "You temper your power with mercy...", alignmentShift: 10 }, { text: "Crush all who oppose you.", nextScene: 'fall_of_bear_clan', impactText: "You choose fear over respect...", alignmentShift: -20 }, ] },
                fall_of_bear_clan: { youtubeId: 'u64_iTQAZyw', text: "The Lion King's forces descend upon the Bear Clan...", choices: [ { text: "Your choices have shaped this world.", nextScene: 'forecast', impactText: "The final battle is inevitable...", alignmentShift: 0 }, ] }
            },
            project_invictus: {
                color: 'var(--blue-accent)',
                start: { youtubeId: '0uoaZZRbwqg', text: "On a futuristic, thriving African continent, the warrior Zeke is haunted by dreams...", choices: [ { text: "Warn the elders of his vision.", nextScene: 'warning', impactText: "You chose foresight. While the council may doubt you...", alignmentShift: 15 }, { text: "Prepare for war alone.", nextScene: 'invasion', impactText: "You chose self-reliance. Trusting only in your own strength...", alignmentShift: -10 }, ] },
                warning: { youtubeId: '4hE3rF_Urh8', text: "The elders dismiss Zeke as a dreamer...", choices: [ { text: "Organize a citizen militia.", nextScene: 'invasion', impactText: "You defy the council and rally the people...", alignmentShift: 20 }, { text: "Accept their judgment.", nextScene: 'invasion', impactText: "You bow to their wisdom, hoping you are wrong...", alignmentShift: -5 }, ] },
                invasion: { youtubeId: 'icIAY_hnQxM', text: "The Roman Galactic Empire attacks. The invasion is swift and brutal...", choices: [ { text: "Your choices have shaped this world.", nextScene: 'forecast', impactText: "The rebellion has begun...", alignmentShift: 0 }, ] }
            }
        };

        // --- 2. DEFINE ALL FUNCTIONS ---
        
        function showScreen(screenName) {
            Object.values(screens).forEach(s => s.classList.add('hidden'));
            const screenToShow = screens[screenName];
            if (screenToShow) {
                screenToShow.classList.remove('hidden');
                screenToShow.classList.remove('opacity-0');
                screenToShow.classList.add('animate-fade-in');
            }
        }

        function typeWriter(el, txt, i = 0) {
            clearTimeout(typeInterval);
            if (i < txt.length) {
                el.innerHTML = txt.substring(0, i + 1) + '<span class="typing-cursor"></span>';
                typeInterval = setTimeout(() => typeWriter(el, txt, i + 1), 30);
            } else {
                el.innerHTML = txt;
                revealChoices();
            }
        }

        function revealChoices() {
            const scene = storyDatabase[currentIP][window.currentSceneKey];
            choiceContainer.innerHTML = '';
            choiceContainer.style.opacity = '0';
            scene.choices.forEach(choice => {
                const button = document.createElement('button');
                button.textContent = choice.text;
                button.className = 'choice-button w-full py-4 rounded-lg text-base font-bold border-2 transition-colors duration-200';
                button.style.backgroundColor = 'var(--current-accent)';
                button.style.borderColor = 'var(--current-accent)';
                button.onmouseover = () => { button.style.backgroundColor = 'transparent'; button.style.color = 'var(--current-accent)'; };
                button.onmouseout = () => { button.style.backgroundColor = 'var(--current-accent)'; button.style.color = 'var(--text-color)'; };
                button.onclick = () => handleChoice(choice);
                choiceContainer.appendChild(button);
            });
            setTimeout(() => { choiceContainer.style.transition = 'opacity 0.5s'; choiceContainer.style.opacity = '1'; }, 100);
        }

        function updateAlignmentMeter() {
            const colorClass = worldAlignment >= 50 ? 'meter-blue' : 'meter-red';
            [alignmentFill, impactMeterFill].forEach(el => {
                if (el) {
                    el.className = `h-full transition-all duration-1000 ease-in-out ${colorClass}`;
                    el.style.width = `${worldAlignment}%`;
                }
            });
        }

        function loadScene(sceneKey) {
            window.currentSceneKey = sceneKey;
            showScreen('demo');
            const ipData = storyDatabase[currentIP];
            const scene = ipData[sceneKey];
            root.style.setProperty('--current-accent', ipData.color);
            if (player && player.loadVideoById) {
                youtubePlayerEl.classList.add('opacity-100');
                player.loadVideoById({ videoId: scene.youtubeId });
            }
            document.getElementById('scene-header').textContent = `[ ${currentIP.replace(/_/g, ' ').toUpperCase()} // NARRATIVE STREAM: ${sceneKey.toUpperCase()} ]`;
            const screenplayEl = document.getElementById('screenplay-text');
            setTimeout(() => typeWriter(screenplayEl, scene.text), 500);
        }

        function handleChoice(choice) {
            worldAlignment = Math.max(0, Math.min(100, worldAlignment + choice.alignmentShift));
            showScreen('impact');
            root.style.setProperty('--current-accent', storyDatabase[currentIP].color);
            document.getElementById('impact-choice-text').textContent = `"${choice.text}"`;
            document.getElementById('impact-consequence-text').textContent = choice.impactText;
            updateAlignmentMeter();
            setTimeout(() => {
                if (choice.nextScene === 'forecast') {
                    loadForecast();
                } else {
                    loadScene(choice.nextScene);
                }
            }, 4000);
        }

        async function initializeFirebase() {
            try {
                // IMPORTANT: Replace this with your own Firebase config object later
                const firebaseConfig = JSON.parse(typeof __firebase_config !== 'undefined' ? __firebase_config : '{}');
                const app = initializeApp(firebaseConfig);
                db = getFirestore(app);
                auth = getAuth(app);

                await new Promise((resolve) => {
                    onAuthStateChanged(auth, async (user) => {
                        if (user) {
                            userId = user.uid;
                            resolve();
                        } else if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
                            await signInWithCustomToken(auth, __initial_auth_token);
                        } else {
                            await signInAnonymously(auth);
                        }
                    });
                });
                
                listenToCanon('bear_by_blade');
                listenToCanon('project_invictus');

            } catch (error) {
                console.error("Firebase initialization failed:", error);
            }
        }

        function listenToCanon(storyId) {
            const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
            const canonDocRef = doc(db, `artifacts/${appId}/public/story_canon`, storyId);

            if (canonUnsubscribe[storyId]) canonUnsubscribe[storyId]();

            canonUnsubscribe[storyId] = onSnapshot(canonDocRef, (docSnap) => {
                let totalAlignment = 50 * 10;
                let playthroughCount = 10;
                
                if (docSnap.exists()) {
                    totalAlignment = docSnap.data().totalAlignment;
                    playthroughCount = docSnap.data().playthroughCount;
                }
                
                const averageAlignment = playthroughCount > 0 ? totalAlignment / playthroughCount : 50;
                updateCanonMeters(storyId, averageAlignment);
            }, (error) => {
                console.error(`Error listening to ${storyId} canon:`, error);
                updateCanonMeters(storyId, 50);
            });
        }

        function updateCanonMeters(storyId, alignment) {
            const bluePercent = Math.round(alignment);
            const redPercent = 100 - bluePercent;

            const blueMeter = document.getElementById(`canon-meter-blue-${storyId}`);
            const redMeter = document.getElementById(`canon-meter-red-${storyId}`);
            const textEl = document.getElementById(`canon-text-${storyId}`);

            if (blueMeter && redMeter) {
                blueMeter.style.width = `${bluePercent}%`;
                redMeter.style.width = `${redPercent}%`;
            }
            if(textEl) {
                 textEl.textContent = `${bluePercent}% Hope/Unity vs ${redPercent}% Vengeance/Conflict`;
            }
        }

        async function loadForecast() {
            showScreen('forecast');
            root.style.setProperty('--current-accent', storyDatabase[currentIP].color);

            document.getElementById('forecast-meter-blue-player').style.width = `${worldAlignment}%`;
            document.getElementById('forecast-meter-red-player').style.width = `${100 - worldAlignment}%`;

            const appId = typeof __app_id !== 'undefined' ? __app_id : 'default-app-id';
            const canonDocRef = doc(db, `artifacts/${appId}/public/story_canon`, currentIP);

            try {
                const newAverageAlignment = await runTransaction(db, async (transaction) => {
                    const canonDoc = await transaction.get(canonDocRef);
                    let totalAlignment = 50 * 10;
                    let playthroughCount = 10;

                    if (canonDoc.exists()) {
                        totalAlignment = canonDoc.data().totalAlignment;
                        playthroughCount = canonDoc.data().playthroughCount;
                    }
                    
                    const newTotalAlignment = totalAlignment + worldAlignment;
                    const newPlaythroughCount = playthroughCount + 1;
                    
                    transaction.set(canonDocRef, { 
                        totalAlignment: newTotalAlignment, 
                        playthroughCount: newPlaythroughCount,
                        lastUpdated: serverTimestamp()
                    }, { merge: true });
                    
                    return newTotalAlignment / newPlaythroughCount;
                });
                
                console.log("Transaction successfully committed!");
                const canonBluePercent = Math.round(newAverageAlignment);
                document.getElementById('forecast-meter-blue-canon').style.width = `${canonBluePercent}%`;
                document.getElementById('forecast-meter-red-canon').style.width = `${100 - canonBluePercent}%`;

            } catch (e) {
                console.error("Transaction failed: ", e);
                const blueMeter = document.getElementById(`canon-meter-blue-${currentIP}`).style.width;
                document.getElementById('forecast-meter-blue-canon').style.width = blueMeter;
                document.getElementById('forecast-meter-red-canon').style.width = document.getElementById(`canon-meter-red-${currentIP}`).style.width;
            }

            document.getElementById('forecast-text').textContent = worldAlignment >= 50 ?
                `Your choices have pushed the world towards unity and hope...` :
                `Your choices have dragged the world deeper into vengeance and conflict...`;
        }

        function setupEventListeners() {
            document.querySelectorAll('.ip-panel').forEach(panel => {
                panel.addEventListener('click', () => {
                    currentIP = panel.dataset.ip;
                    worldAlignment = 50;
                    updateAlignmentMeter();
                    loadScene('start');
                });
            });
            backButton.addEventListener('click', (e) => {
                e.preventDefault();
                if (player && player.stopVideo) player.stopVideo();
                youtubePlayerEl.classList.remove('opacity-100');
                showScreen('hub');
            });
            restartButton.addEventListener('click', (e) => {
                e.preventDefault();
                showScreen('hub');
            });
            const restartBtn = document.getElementById('restart-button');
            restartBtn.style.borderColor = 'var(--current-accent)';
            restartBtn.style.backgroundColor = 'var(--current-accent)';
            restartBtn.onmouseover = () => { restartBtn.style.backgroundColor = 'transparent'; restartBtn.style.color = 'var(--current-accent)'; };
            restartBtn.onmouseout = () => { restartBtn.style.backgroundColor = 'var(--current-accent)'; restartBtn.style.color = 'var(--text-color)'; };
        }

        window.onYouTubeIframeAPIReady = function() {
            player = new YT.Player('youtube-player', {
                height: '100%',
                width: '100%',
                playerVars: { 'autoplay': 1, 'controls': 0, 'showinfo': 0, 'rel': 0, 'loop': 1, 'mute': 1, 'playsinline': 1 },
                events: { 'onReady': (event) => event.target.mute() }
            });
        }
        
        // --- 3. DEFINE THE MAIN APP ENTRY POINT ---

        async function main() {
            setupEventListeners();
            await initializeFirebase();
            
            const tag = document.createElement('script');
            tag.src = "https://www.youtube.com/iframe_api";
            document.head.appendChild(tag);
            
            setTimeout(() => showScreen('hub'), 3000);
        }

        // --- 4. RUN THE APP ---
        main();

    </script>
</body>
</html>


