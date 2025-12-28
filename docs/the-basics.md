<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>FunnyReels AI</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        :root { --neon-blue: #00f2ff; }
        body { background-color: #050505; color: white; overflow: hidden; }
        .glass-card {
            background: rgba(255, 255, 255, 0.05);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 24px;
        }
        .video-container { height: 100vh; width: 100%; position: relative; }
    </style>
</head>
<body>

    <div class="max-w-md mx-auto border-x border-zinc-800 h-screen relative bg-zinc-900">
        
        <div class="absolute top-0 w-full p-6 z-20 flex justify-between items-center bg-gradient-to-b from-black/60 to-transparent">
            <h1 class="font-black tracking-tighter text-xl">REELS.AI</h1>
            <div id="ai-status" class="px-3 py-1 rounded-full bg-red-500/20 text-[10px] text-red-500 border border-red-500/50">
                AI OFFLINE
            </div>
        </div>

        <div class="video-container flex items-center justify-center">
            <div class="text-center p-10">
                <p class="text-zinc-500 mb-4 italic">"Video Feed Loading..."</p>
                <div class="w-12 h-12 border-4 border-blue-500 border-t-transparent rounded-full animate-spin mx-auto"></div>
            </div>
        </div>

        <div class="absolute bottom-0 w-full p-6 z-20 bg-gradient-to-t from-black to-transparent">
            <div class="flex items-end justify-between">
                <div>
                    <p class="font-bold">@Admin_Funny</p>
                    <p class="text-xs text-zinc-400">Capturing your laughter in real-time...</p>
                </div>
                <div class="flex flex-col gap-4">
                    <button class="glass-card p-3">❤️</button>
                    <button class="glass-card p-3">💬</button>
                </div>
            </div>
        </div>
    </div>

    <video id="video" autoplay muted playsinline class="hidden"></video>

    <script>
        // Check if elements exist to prevent errors
        const video = document.getElementById('video');
        const status = document.getElementById('ai-status');

        async function initCamera() {
            try {
                const stream = await navigator.mediaDevices.getUserMedia({ video: true });
                video.srcObject = stream;
                status.innerText = "AI MONITORING";
                status.classList.replace('text-red-500', 'text-cyan-400');
                status.classList.replace('bg-red-500/20', 'bg-cyan-500/20');
                console.log("Camera active");
            } catch (err) {
                console.error("Error accessing camera:", err);
                status.innerText = "CAMERA BLOCKED";
            }
        }

        // Start when page loads
        window.addEventListener('DOMContentLoaded', initCamera);
    </script>
</body>
</html>

