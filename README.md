<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Link Start! - Personal Page</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Rubik:wght@400;500;700&display=swap" rel="stylesheet">
    <style>
        :root {
            /* SAO 风格配色 */
            --primary-color: #5BC0EB; /* 天空蓝 */
            --accent-color: #FDE74C;  /* 像 UI 里的黄色高亮 */
            --glass-bg: rgba(255, 255, 255, 0.15);
            --glass-border: rgba(255, 255, 255, 0.3);
            --text-main: #ffffff;
            --text-sub: #e0e0e0;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Rubik', sans-serif;
        }

        body {
            height: 100vh;
            width: 100vw;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
            /* 背景图：SAO 艾恩葛朗特风景 */
            background: url('https://images.alphacoders.com/605/thumb-1920-605592.png') no-repeat center center/cover;
            position: relative;
        }

        /* 加一层深色遮罩，保证文字清晰 */
        body::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 20, 40, 0.3); /* 深蓝微透 */
            z-index: 0;
        }

        /* 核心卡片容器 */
        .card {
            position: relative;
            z-index: 10;
            width: 380px;
            padding: 40px;
            border-radius: 24px;
            /* 玻璃拟态核心代码 */
            background: var(--glass-bg);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid var(--glass-border);
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.3);
            
            display: flex;
            flex-direction: column;
            align-items: center;
            text-align: center;
            transition: transform 0.2s ease;
            animation: fadeInUps 1s ease-out;
        }

        /* 3D 浮动效果 */
        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 15px 40px 0 rgba(0, 0, 0, 0.4);
            border-color: rgba(255, 255, 255, 0.6);
        }

        /* 头像框 */
        .avatar-container {
            width: 120px;
            height: 120px;
            margin-bottom: 20px;
            position: relative;
        }

        .avatar {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            object-fit: cover;
            border: 3px solid rgba(255, 255, 255, 0.8);
            box-shadow: 0 0 20px rgba(91, 192, 235, 0.5); /* 蓝色光晕 */
        }

        /* SAO 风格的状态点 (Online) */
        .status-dot {
            position: absolute;
            bottom: 5px;
            right: 5px;
            width: 20px;
            height: 20px;
            background: #00ff00; /* 绿色水晶 */
            border-radius: 50%;
            border: 3px solid rgba(255, 255, 255, 0.3);
            box-shadow: 0 0 10px #00ff00;
        }

        /* 名字和简介 */
        .name {
            color: var(--text-main);
            font-size: 28px;
            font-weight: 700;
            margin-bottom: 8px;
            letter-spacing: 1px;
            text-shadow: 0 2px 4px rgba(0,0,0,0.5);
        }

        .bio {
            color: var(--text-sub);
            font-size: 14px;
            margin-bottom: 30px;
            line-height: 1.6;
            background: rgba(0, 0, 0, 0.2); /* 文字背景条，像游戏HUD */
            padding: 5px 15px;
            border-radius: 12px;
        }

        /* 链接按钮组 */
        .social-links {
            display: flex;
            gap: 15px;
            width: 100%;
            justify-content: center;
        }

        .btn {
            width: 45px;
            height: 45px;
            border-radius: 12px;
            background: rgba(255, 255, 255, 0.1);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            text-decoration: none;
            font-size: 20px;
            transition: all 0.3s ease;
            border: 1px solid rgba(255,255,255,0.1);
        }

        .btn:hover {
            background: var(--primary-color);
            transform: scale(1.1);
            box-shadow: 0 0 15px var(--primary-color);
        }

        /* 底部 Link Start 按钮 */
        .action-btn {
            margin-top: 30px;
            padding: 12px 40px;
            background: linear-gradient(90deg, #00C6FF, #0072FF);
            color: white;
            border-radius: 30px;
            text-decoration: none;
            font-weight: bold;
            box-shadow: 0 4px 15px rgba(0, 114, 255, 0.4);
            transition: 0.3s;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .action-btn:hover {
            background: linear-gradient(90deg, #0072FF, #00C6FF);
            box-shadow: 0 6px 20px rgba(0, 114, 255, 0.6);
            transform: translateY(-2px);
        }

        /* 粒子特效背景 (纯CSS模拟) */
        .particle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: rgba(255,255,255,0.5);
            border-radius: 50%;
            animation: float 10s infinite linear;
            z-index: 1;
        }

        @keyframes float {
            0% { transform: translateY(100vh) scale(0); opacity: 0; }
            50% { opacity: 1; }
            100% { transform: translateY(-100px) scale(1); opacity: 0; }
        }

        @keyframes fadeInUps {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* 移动端适配 */
        @media (max-width: 480px) {
            .card { width: 90%; padding: 30px; }
        }
    </style>
</head>
<body>

    <div id="particles"></div>

    <div class="card">
        <div class="avatar-container">
            <img src="https://i.pinimg.com/736x/8f/1a/0d/8f1a0d33261642233f24021703649520.jpg" alt="Avatar" class="avatar">
            <div class="status-dot"></div>
        </div>

        <h1 class="name">Kirito</h1>

        <p class="bio">
            Level 96 • Dual Wielder<br>
            Exploring the Virtual World
        </p>

        <div class="social-links">
            <a href="#" class="btn"><i class="fa-brands fa-github"></i></a>
            <a href="#" class="btn"><i class="fa-brands fa-twitter"></i></a>
            <a href="#" class="btn"><i class="fa-brands fa-bilibili"></i></a>
            <a href="#" class="btn"><i class="fa-solid fa-envelope"></i></a>
        </div>

        <a href="#" class="action-btn">Link Start</a>
    </div>

    <script>
        // 简单的粒子生成脚本
        const particleContainer = document.getElementById('particles');
        const particleCount = 30;

        for (let i = 0; i < particleCount; i++) {
            const particle = document.createElement('div');
            particle.classList.add('particle');
            
            // 随机位置和大小
            const size = Math.random() * 5 + 2;
            particle.style.width = `${size}px`;
            particle.style.height = `${size}px`;
            particle.style.left = `${Math.random() * 100}vw`;
            
            // 随机动画时长和延迟
            const duration = Math.random() * 10 + 5;
            const delay = Math.random() * 5;
            particle.style.animationDuration = `${duration}s`;
            particle.style.animationDelay = `-${delay}s`; // 负延迟让动画一开始就铺满屏幕
            
            particleContainer.appendChild(particle);
        }

        // 卡片 3D 视差微动效果
        const card = document.querySelector('.card');
        document.addEventListener('mousemove', (e) => {
            const xAxis = (window.innerWidth / 2 - e.pageX) / 25;
            const yAxis = (window.innerHeight / 2 - e.pageY) / 25;
            card.style.transform = `rotateY(${xAxis}deg) rotateX(${yAxis}deg)`;
        });
    </script>
</body>
</html>
