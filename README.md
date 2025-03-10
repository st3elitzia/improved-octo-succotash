<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>小瑶专属表白</title>
    <style>
        /* 设置背景图片 */
        body {
            margin: 0;
            padding: 0;
            height: 100vh;
            background: url('1.jpg') center/cover; /* 替换为你的图片文件名 */
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: 'Microsoft YaHei', sans-serif;
            overflow: hidden;
        }

        /* 容器样式 */
        .container {
            text-align: center;
            background: rgba(255, 255, 255, 0.9); /* 半透明背景 */
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 0 20px rgba(255, 105, 180, 0.3);
        }

        /* 中间图片样式 */
        .kitty-img {
            width: 150px;
            height: auto;
            margin-bottom: 20px;
            transition: transform 0.3s ease; /* 图片缩放动画 */
        }

        /* 标题样式 */
        h1 {
            color: #ff69b4;
            margin: 20px 0;
            font-size: 28px;
        }

        /* 按钮样式 */
        .buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 20px;
        }

        button {
            background: #ff69b4;
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 25px;
            font-size: 18px;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        #yesBtn {
            background: #ff69b4;
        }

        #noBtn {
            background: #f0f0f0;
            color: #666;
            border: 2px solid #ff69b4;
        }
    </style>
</head>
<body>

<div class="container">
    <img id="kittyImage" src="hello-kitty.png" alt="Hello Kitty" class="kitty-img"> <!-- 初始图片 -->
    <h1>亲爱的小瑶，你愿意成为我的唯一吗？🌸</h1>
    <div class="buttons">
        <button id="yesBtn">愿意</button>
        <button id="noBtn">不愿意</button>
    </div>
</div>

<script>
    // 图片列表（每次点击“不愿意”按钮时切换）
    const images = [
        "kitty1.jpg", // 第一次点击显示的图片
        "kitty2.jpg", // 第二次点击显示的图片
        "kitty3.jpg", // 第三次点击显示的图片
        "kitty1.jpg", // 第四次点击显示的图片
        "kitty2.jpg", // 第五次点击显示的图片
        "kitty3.jpg", // 第六次点击显示的图片
        "kitty1.jpg", // 第七次点击显示的图片
        "kitty2.jpg", // 第八次点击显示的图片
        "kitty4.jpg", // 第九次点击显示的图片
        "kitty5.jpg" // 第十次点击显示的图片
    ];

    let noClickCount = 0;
    const maxClicks = 10;
    const yesBtn = document.getElementById('yesBtn');
    const noBtn = document.getElementById('noBtn');
    const kittyImage = document.getElementById('kittyImage');

    // 点击“愿意”按钮
    yesBtn.addEventListener('click', () => {
        alert("我最喜欢你啦 ❤️");
    });

    // 点击“不愿意”按钮
    noBtn.addEventListener('click', () => {
        noClickCount++;

        if (noClickCount <= maxClicks) {
            // 动态调整“愿意”按钮大小
            const yesScale = 1 + (noClickCount * 0.1); // 每次点击放大 0.1 倍
            yesBtn.style.transform = `scale(${Math.min(yesScale, 2)})`; // 最大放大到 2 倍

            // 动态调整“不愿意”按钮大小
            const noScale = 1 - (noClickCount * 0.1); // 每次点击缩小 0.1 倍
            noBtn.style.transform = `scale(${Math.max(noScale, 0.5)})`; // 最小缩小到 0.5 倍

            // 更换中间图片
            if (noClickCount <= images.length) {
                kittyImage.src = images[noClickCount - 1];
            }

            // 放大中间图片
            const imageScale = 1 + (noClickCount * 0.1); // 每次点击放大 0.1 倍
            kittyImage.style.transform = `scale(${Math.min(imageScale, 1.5)})`; // 最大放大到 1.5 倍

            // 最后一次点击时隐藏“不愿意”按钮
            if (noClickCount === maxClicks) {
                noBtn.style.display = 'none';
                yesBtn.style.width = '65%';
                yesBtn.innerHTML = '就知道你躲不掉啦❤️';
            }
        }
    });
</script>

</body>
</html>
