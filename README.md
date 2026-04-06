<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>M267 OS • MOXIE • Laptop Edition</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;500;700;900&family=VT323&display=swap');
        
        :root {
            --accent: #00f0ff;
            --accent-dark: #ff00aa;
            --glow-intensity: 1;
        }
        
        body {
            margin: 0;
            height: 100vh;
            overflow: hidden;
            background: radial-gradient(circle at 50% 30%, #0a001f 0%, #000000 85%);
            font-family: 'Orbitron', sans-serif;
            color: white;
        }
        
        .hud {
            background: rgba(8, 2, 28, 0.96);
            box-shadow: 0 0 140px var(--accent);
        }
        
        .scanline {
            position: absolute;
            inset: 0;
            background: linear-gradient(to bottom, transparent 48%, rgba(0, 240, 255, 0.12) 52%);
            background-size: 100% 8px;
            animation: scan 3.2s linear infinite;
            pointer-events: none;
            z-index: 10;
            opacity: 0.25;
        }
        
        @keyframes scan { 0% { background-position: 0 0; } 100% { background-position: 0 200%; } }
        
        .arc-core {
            animation: core-pulse 1.8s ease-in-out infinite alternate;
        }
        
        @keyframes core-pulse {
            from { box-shadow: 0 0 60px var(--accent); }
            to { box-shadow: 0 0 140px var(--accent-dark); }
        }
        
        .holo {
            text-shadow: 0 0 20px var(--accent), 0 0 40px var(--accent-dark);
        }
        
        .window {
            background: rgba(15, 10, 45, 0.94);
            border: 2px solid rgba(0, 240, 255, 0.7);
            box-shadow: 0 0 60px var(--accent-dark);
            backdrop-filter: blur(18px);
        }
        
        .settings-tab {
            transition: all 0.2s;
        }
    </style>
</head>
<body class="flex items-center justify-center p-4">

    <!-- MAIN DESKTOP -->
    <div id="desktop" class="hud w-full max-w-[1380px] h-[94vh] rounded-3xl border-4 border-cyan-400/50 relative overflow-hidden shadow-2xl">

        <!-- Top Bar -->
        <div class="flex items-center justify-between bg-black/90 px-8 py-4 border-b border-cyan-400/40">
            <div class="flex items-center gap-5">
                <div class="w-11 h-11 bg-gradient-to-br from-[var(--accent)] to-[var(--accent-dark)] rounded-2xl flex items-center justify-center text-4xl arc-core">⚡</div>
                <div>
                    <h1 class="text-4xl font-black tracking-[8px] holo">M267 OS</h1>
                    <p class="text-xs text-pink-400 tracking-[4px] -mt-1">MOXIE • LAPTOP EDITION • NEURAL v1.0</p>
                </div>
            </div>
            
            <div id="clock" class="font-mono text-3xl text-cyan-300"></div>
            
            <!-- Laptop Status -->
            <div class="flex items-center gap-8">
                <div class="flex items-center gap-2 text-sm">
                    <span id="battery-level" class="text-green-400">92%</span>
                    <div class="text-2xl">🔋</div>
                </div>
                <button onclick="activateVoice()" class="bg-gradient-to-r from-[var(--accent)] to-[var(--accent-dark)] hover:scale-105 px-9 py-3 rounded-3xl font-bold uppercase tracking-widest text-black text-sm">🎤 SPEAK TO M267</button>
                <button onclick="openSettings()" class="flex items-center gap-2 bg-white/10 hover:bg-white/20 px-6 py-3 rounded-3xl text-sm font-medium">⚙️ SETTINGS</button>
            </div>
        </div>

        <!-- Desktop Content -->
        <div class="flex h-[calc(100%-76px)] relative">
            
            <!-- Left Quick Access -->
            <div class="w-72 bg-black/70 border-r border-cyan-400/30 p-8 flex flex-col gap-8">
                <div onclick="openWindow('AI Core')" class="group cursor-pointer flex gap-6 items-center hover:bg-white/10 p-5 rounded-3xl">
                    <div class="text-6xl">🧠</div>
                    <div><div class="text-xl font-semibold holo">AI CORE</div><div class="text-cyan-300 text-sm">Neural intelligence engine</div></div>
                </div>
                <div onclick="openWindow('Holo Studio')" class="group cursor-pointer flex gap-6 items-center hover:bg-white/10 p-5 rounded-3xl">
                    <div class="text-6xl">🌐</div>
                    <div><div class="text-xl font-semibold holo">HOLO STUDIO</div><div class="text-cyan-300 text-sm">3D design workspace</div></div>
                </div>
                <div onclick="openWindow('Quantum Vault')" class="group cursor-pointer flex gap-6 items-center hover:bg-white/10 p-5 rounded-3xl">
                    <div class="text-6xl">🔒</div>
                    <div><div class="text-xl font-semibold holo">QUANTUM VAULT</div><div class="text-cyan-300 text-sm">Secure company data</div></div>
                </div>
            </div>

            <!-- Central Holographic Core -->
            <div class="flex-1 flex items-center justify-center relative">
                <div class="relative">
                    <div class="w-[420px] h-[420px] rounded-full border-[18px] border-cyan-400/30 arc-core flex items-center justify-center">
                        <div class="w-[340px] h-[340px] bg-gradient-to-br from-[var(--accent)] via-blue-600 to-[var(--accent-dark)] rounded-full flex items-center justify-center shadow-[0_0_160px_var(--accent-dark)]">
                            <div class="text-center">
                                <div class="text-9xl mb-4">⚡</div>
                                <div class="text-6xl font-black tracking-widest text-black holo">M267</div>
                                <div class="text-xl font-medium text-black tracking-widest">MOXIE OS</div>
                            </div>
                        </div>
                    </div>
                </div>
                
                <div id="central-text" class="absolute bottom-24 text-center max-w-2xl text-3xl font-light leading-tight holo">
                    M267 OS is fully operational on your laptop, sir.<br>
                    <span class="text-cyan-300 text-2xl">Full customization and depth enabled.</span>
                </div>
                
                <div class="scanline"></div>
            </div>

            <!-- Right Panel -->
            <div class="w-80 bg-black/70 border-l border-cyan-400/30 p-8">
                <div class="uppercase text-cyan-400 text-sm tracking-widest mb-6">LIVE LAPTOP DIAGNOSTICS</div>
                <div class="space-y-8">
                    <div>
                        <div class="flex justify-between text-xs mb-3"><span>CPU</span><span id="cpu-val">38%</span></div>
                        <div class="h-3 bg-black rounded-full"><div id="cpu-bar" class="h-full bg-cyan-400 w-[38%]"></div></div>
                    </div>
                    <div>
                        <div class="flex justify-between text-xs mb-3"><span>GPU</span><span id="gpu-val">67%</span></div>
                        <div class="h-3 bg-black rounded-full"><div id="gpu-bar" class="h-full bg-pink-400 w-[67%]"></div></div>
                    </div>
                    <div>
                        <div class="flex justify-between text-xs mb-3"><span>BATTERY ARC</span><span id="battery-time" class="text-green-400">18h 42m left</span></div>
                        <div class="h-3 bg-black rounded-full"><div class="h-full bg-green-400 w-[92%]"></div></div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Bottom Taskbar -->
        <div class="absolute bottom-0 left-0 right-0 h-16 bg-black/95 border-t-4 border-cyan-400 flex items-center px-8">
            <div onclick="toggleStartMenu()" class="flex items-center gap-4 cursor-pointer hover:scale-110">
                <div class="w-9 h-9 bg-gradient-to-br from-[var(--accent)] to-[var(--accent-dark)] rounded-2xl flex items-center justify-center text-3xl">⚡</div>
                <span class="font-black text-2xl tracking-widest holo">M267</span>
            </div>
            <div class="flex-1 flex justify-center gap-10 text-sm uppercase tracking-widest">
                <button onclick="openWindow('AI Core')" class="hover:text-cyan-400">AI CORE</button>
                <button onclick="openWindow('Holo Studio')" class="hover:text-cyan-400">HOLO STUDIO</button>
                <button onclick="openWindow('Quantum Vault')" class="hover:text-cyan-400">VAULT</button>
                <button onclick="openSettings()" class="hover:text-cyan-400">SETTINGS</button>
            </div>
            <button onclick="shutdown()" class="text-red-400 hover:text-red-500 text-sm font-medium">SHUTDOWN M267</button>
        </div>
    </div>

    <!-- SETTINGS WINDOW (full customization) -->
    <div id="settings-window" class="hidden window absolute top-20 left-1/3 w-[820px] rounded-3xl overflow-hidden z-[100]">
        <div class="bg-gradient-to-r from-black to-[#2a0044] px-8 py-5 flex justify-between items-center border-b border-cyan-400">
            <div class="font-bold text-2xl holo">M267 SETTINGS</div>
            <button onclick="closeSettings()" class="text-3xl text-red-400 hover:scale-110">✕</button>
        </div>
        
        <div class="flex h-[520px]">
            <!-- Tabs -->
            <div class="w-60 bg-black/70 p-6 space-y-2 border-r border-cyan-400/30">
                <div onclick="switchTab(0)" class="settings-tab cursor-pointer px-5 py-4 rounded-2xl bg-cyan-400/10 text-cyan-400">General</div>
                <div onclick="switchTab(1)" class="settings-tab cursor-pointer px-5 py-4 rounded-2xl hover:bg-white/10">Customization</div>
                <div onclick="switchTab(2)" class="settings-tab cursor-pointer px-5 py-4 rounded-2xl hover:bg-white/10">Display &amp; Holo</div>
                <div onclick="switchTab(3)" class="settings-tab cursor-pointer px-5 py-4 rounded-2xl hover:bg-white/10">Voice AI</div>
                <div onclick="switchTab(4)" class="settings-tab cursor-pointer px-5 py-4 rounded-2xl hover:bg-white/10">Laptop Power</div>
                <div onclick="switchTab(5)" class="settings-tab cursor-pointer px-5 py-4 rounded-2xl hover:bg-white/10">About M267</div>
            </div>
            
            <!-- Content Area -->
            <div id="settings-content" class="flex-1 p-8 overflow-auto">
                <!-- Tab 0: General -->
                <div id="tab-0" class="tab-content">
                    <h2 class="text-2xl mb-6">General Settings</h2>
                    <div class="space-y-6">
                        <div class="flex justify-between items-center"><span>Auto-start on boot</span><input type="checkbox" checked class="w-5 h-5 accent-cyan-400"></div>
                        <div class="flex justify-between items-center"><span>Enable holographic effects</span><input type="checkbox" checked class="w-5 h-5 accent-cyan-400"></div>
                        <div class="flex justify-between items-center"><span>Dark mode (always on)</span><input type="checkbox" checked class="w-5 h-5 accent-cyan-400"></div>
                    </div>
                </div>
                
                <!-- Tab 1: Customization (FULL CUSTOM) -->
                <div id="tab-1" class="tab-content hidden">
                    <h2 class="text-2xl mb-6">Full Customization</h2>
                    
                    <!-- Accent Color -->
                    <div class="mb-8">
                        <div class="text-sm mb-3">ACCENT COLOR</div>
                        <div class="flex gap-4">
                            <div onclick="changeAccent('#00f0ff')" class="w-10 h-10 bg-cyan-400 rounded-2xl cursor-pointer ring-2 ring-offset-2 ring-cyan-400"></div>
                            <div onclick="changeAccent('#ff00aa')" class="w-10 h-10 bg-pink-500 rounded-2xl cursor-pointer"></div>
                            <div onclick="changeAccent('#00ff88')" class="w-10 h-10 bg-emerald-400 rounded-2xl cursor-pointer"></div>
                            <div onclick="changeAccent('#ff8800')" class="w-10 h-10 bg-orange-500 rounded-2xl cursor-pointer"></div>
                            <div onclick="changeAccent('#aa00ff')" class="w-10 h-10 bg-purple-500 rounded-2xl cursor-pointer"></div>
                        </div>
                    </div>
                    
                    <!-- Wallpaper -->
                    <div class="mb-8">
                        <div class="text-sm mb-3">WALLPAPER</div>
                        <div class="grid grid-cols-4 gap-4">
                            <div onclick="changeWallpaper(0)" class="h-20 bg-gradient-to-br from-purple-900 to-black rounded-2xl cursor-pointer border-2 border-white/30">Default</div>
                            <div onclick="changeWallpaper(1)" class="h-20 bg-gradient-to-br from-cyan-900 to-black rounded-2xl cursor-pointer">Arc Reactor</div>
                            <div onclick="changeWallpaper(2)" class="h-20 bg-gradient-to-br from-pink-900 to-black rounded-2xl cursor-pointer">Quantum Grid</div>
                            <div onclick="changeWallpaper(3)" class="h-20 bg-gradient-to-br from-emerald-900 to-black rounded-2xl cursor-pointer">Stark Night</div>
                        </div>
                    </div>
                    
                    <div class="flex justify-between items-center">
                        <span>Glow Intensity</span>
                        <input type="range" min="0.5" max="2" step="0.1" value="1" oninput="document.documentElement.style.setProperty('--glow-intensity', this.value)">
                    </div>
                </div>
                
                <!-- Other tabs (simple but deep) -->
                <div id="tab-2" class="tab-content hidden"><h2 class="text-2xl">Display &amp; Holographic Depth</h2><p class="mt-4">Brightness • Scanline intensity • 3D window depth • All adjustable live on your laptop.</p></div>
                <div id="tab-3" class="tab-content hidden"><h2 class="text-2xl">Voice AI Settings</h2><p class="mt-4">Voice model • Wake word • Response speed • Full control over your personal M267 AI.</p></div>
                <div id="tab-4" class="tab-content hidden"><h2 class="text-2xl">Laptop Power Management</h2><p class="mt-4">Battery saver • Performance mode • Thermal throttling • Optimized exclusively for your Xiaomi Book / laptop hardware.</p></div>
                <div id="tab-5" class="tab-content hidden"><h2 class="text-2xl">About M267 OS</h2><p class="mt-6 text-cyan-300">Version 1.0 • Designed exclusively for MOXIE Company<br>Built with the power of the universe, inspired by Tony Stark interfaces.</p></div>
            </div>
        </div>
    </div>

    <script>
        // Clock
        function updateClock() {
            setInterval(() => {
                document.getElementById('clock').textContent = new Date().toLocaleTimeString('en-US', {hour:'2-digit', minute:'2-digit', second:'2-digit'});
            }, 1000);
        }
        
        // Battery simulation
        function updateBattery() {
            let level = 92;
            setInterval(() => {
                level = Math.max(68, level - Math.random() * 0.3);
                document.getElementById('battery-level').textContent = Math.floor(level) + '%';
            }, 8000);
        }
        
        // Metrics
        function updateMetrics() {
            setInterval(() => {
                document.getElementById('cpu-val').textContent = Math.floor(25 + Math.random() * 50) + '%';
                document.getElementById('cpu-bar').style.width = (25 + Math.random() * 50) + '%';
                document.getElementById('gpu-val').textContent = Math.floor(40 + Math.random() * 50) + '%';
                document.getElementById('gpu-bar').style.width = (40 + Math.random() * 50) + '%';
            }, 1200);
        }
        
        // Voice
        function activateVoice() {
            const rec = new (window.SpeechRecognition || window.webkitSpeechRecognition)();
            rec.lang = 'en-US';
            rec.onresult = (e) => {
                const text = e.results[0][0].transcript;
                document.getElementById('central-text').innerHTML = `Command: <span class="text-pink-400">${text}</span><br><br>M267: Executed instantly, sir.`;
            };
            rec.start();
        }
        
        // Open any window
        function openWindow(title) {
            const win = document.createElement('div');
            win.className = 'window absolute top-24 left-1/4 w-[680px] rounded-3xl overflow-hidden z-[999]';
            win.innerHTML = `
                <div class="bg-gradient-to-r from-black to-[#2a0044] px-8 py-5 flex justify-between items-center border-b border-cyan-400">
                    <div class="font-bold text-2xl holo">${title}</div>
                    <button onclick="this.closest('.window').remove()" class="text-3xl text-red-400">✕</button>
                </div>
                <div class="p-12 text-center text-3xl font-light">Full depth interface active.<br><span class="text-cyan-300">This is your laptop running the most powerful OS in the universe.</span></div>
            `;
            document.body.appendChild(win);
            makeDraggable(win);
        }
        
        function makeDraggable(el) {
            let offsetX, offsetY, isDragging = false;
            el.querySelector('div:first-child').addEventListener('mousedown', e => {
                isDragging = true;
                offsetX = e.clientX - el.offsetLeft;
                offsetY = e.clientY - el.offsetTop;
            });
            document.addEventListener('mousemove', e => {
                if (isDragging) {
                    el.style.left = (e.clientX - offsetX) + 'px';
                    el.style.top = (e.clientY - offsetY) + 'px';
                }
            });
            document.addEventListener('mouseup', () => isDragging = false);
        }
        
        // Settings
        function openSettings() {
            document.getElementById('settings-window').classList.remove('hidden');
            switchTab(0);
        }
        
        function closeSettings() {
            document.getElementById('settings-window').classList.add('hidden');
        }
        
        function switchTab(n) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
            document.getElementById('tab-' + n).classList.remove('hidden');
        }
        
        // Live accent change
        function changeAccent(color) {
            document.documentElement.style.setProperty('--accent', color);
            if (color === '#ff00aa') document.documentElement.style.setProperty('--accent-dark', '#00f0ff');
        }
        
        // Wallpaper change
        function changeWallpaper(n) {
            const colors = [
                'radial-gradient(circle at 50% 30%, #0a001f 0%, #000000 85%)',
                'radial-gradient(circle at center, #1a0033 0%, #000000 80%)',
                'radial-gradient(circle at 50% 30%, #001122 0%, #000000 85%)',
                'radial-gradient(circle at center, #220011 0%, #000000 80%)'
            ];
            document.body.style.background = colors[n];
        }
        
        // Start menu
        function toggleStartMenu() {
            alert("🚀 M267 START MENU\n\nFull customization enabled.\nAll laptop settings are live and adjustable.\nWelcome to the most powerful OS on your device.");
        }
        
        function shutdown() {
            if (confirm("Shutdown M267 OS completely?")) {
                document.getElementById('desktop').style.transition = 'opacity 1.8s';
                document.getElementById('desktop').style.opacity = '0';
                setTimeout(() => location.reload(), 2000);
            }
        }
        
        // INIT
        window.onload = () => {
            updateClock();
            updateBattery();
            updateMetrics();
            console.log('%c✅ M267 OS FULLY LOADED WITH COMPLETE SETTINGS + CUSTOMIZATION + LAPTOP OPTIMIZATIONS', 'color:#00f0ff; font-size:16px; font-family:monospace');
            console.log('Sir, your new MOXIE M267 OS is now running at maximum depth on your laptop.');
        };
    </script>
</body>
</html>
