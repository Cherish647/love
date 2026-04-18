<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>❤️ 专属浪漫 ❤️</title>
    <style>
        body {
            margin: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background-color: #FFE4E1;
            font-family: 'Microsoft YaHei', sans-serif;
            overflow: hidden;
            touch-action: none;
        }
        .container {
            text-align: center;
            background: rgba(255, 255, 255, 0.9);
            padding: 40px 30px;
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
            z-index: 10;
            width: 80%;
            max-width: 400px;
        }
        h1 { color: #FF1493; font-size: 1.5rem; margin-bottom: 30px; }
        .buttons { 
            display: flex;
            justify-content: space-around;
            align-items: center;
            height: 100px; 
            position: relative;
        }
        button {
            padding: 12px 25px;
            font-size: 16px;
            border-radius: 10px;
            border: none;
            cursor: pointer;
            transition: all 0.2s;
            z-index: 11;
        }
        #yes { background-color: #FF69B4; color: white; }
        #no {
            background-color: #CCCCCC; color: #666;
            position: absolute;
            white-space: nowrap;
        }
        .message-box {
            position: fixed;
            padding: 10px 20px;
            background: #FFB6C1;
            color: #8B0000;
            font-size: 14px;
            font-weight: bold;
            border-radius: 50px;
            box-shadow: 2px 2px 10px rgba(0,0,0,0.1);
            z-index: 100;
            animation: pop 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            pointer-events: none;
        }
        @keyframes pop {
            0% { transform: scale(0); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }
    </style>
</head>
<body>

    <div class="container" id="main">
        <h1>可以成为我的恋人吗？ ❤️</h1>
        <div class="buttons">
            <button id="yes">可以 ❤️</button>
            <button id="no">不可以</button>
        </div>
    </div>

    <script>
        const messages = [
            "我想你了! ❤️", "多喝水哦", "保持微笑呀", "每天都要元气满满呢",
            "记得吃水果", "保持好心情", "好好爱自己", "梦想成真",
            "遇见你是我最大的幸运!", "我会一直陪在你身边的! 🌟",
            "你超棒的！", "要相信自己", "你笑起来真好看"
        ];

        const noBtn = document.getElementById('no');
        const yesBtn = document.getElementById('yes');

        // 让按钮跳走的函数
        function moveButton() {
            const padding = 50;
            const x = Math.random() * (window.innerWidth - noBtn.offsetWidth - padding * 2) + padding;
            const y = Math.random() * (window.innerHeight - noBtn.offsetHeight - padding * 2) + padding;
            
            noBtn.style.left = x + 'px';
            noBtn.style.top = y + 'px';
            noBtn.style.position = 'fixed'; // 变成绝对定位才能到处跳
        }

        // 适配鼠标和手指触摸
        noBtn.addEventListener('mouseover', moveButton);
        noBtn.addEventListener('touchstart', (e) => {
            e.preventDefault();
            moveButton();
        });

        // 点击“可以”
        yesBtn.onclick = function() {
            document.getElementById('main').style.display = 'none';
            
            // 快速生成随机情话弹窗
            let count = 0;
            const maxMessages = 40;
            const interval = setInterval(() => {
                createMessage();
                count++;
                if (count >= maxMessages) clearInterval(interval);
            }, 150);
        };

        function createMessage() {
            const div = document.createElement('div');
            div.className = 'message-box';
            div.innerText = messages[Math.floor(Math.random() * messages.length)];
            
            const x = Math.random() * (window.innerWidth - 150);
            const y = Math.random() * (window.innerHeight - 50);
            
            div.style.left = x + 'px';
            div.style.top = y + 'px';
            // 随机颜色
            const hue = Math.random() * 20 + 340; // 粉色系
            div.style.backgroundColor = `hsl(${hue}, 100%, 85%)`;
            
            document.body.appendChild(div);
        }
    </script>
</body>
</html>
