<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <title>For Ever</title>
    <style>
        body {
            margin: 0;
            background-color: black;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        canvas {
            display: block;
        }
        /* تنسيق النصوص باللون الوردي وضبط المسافات */
        #topText {
            position: absolute;
            top: 10%; /* تم رفعه للأعلى أكثر */
            font-size: 35px;
            font-weight: bold;
            color: pink; /* تغيير اللون للوردي */
            text-shadow: 0 0 10px rgba(255, 192, 203, 0.5); /* إضافة توهج بسيط */
        }
        #bottomText {
            position: absolute;
            bottom: 10%; /* تم تنزيله للأسفل أكثر */
            font-size: 25px;
            color: pink; /* تغيير اللون للوردي */
            letter-spacing: 2px;
        }
    </style>
</head>
<body>

    <div id="topText">I Love You Rahma</div>
    <canvas id="heartCanvas"></canvas>
    <div id="bottomText">By Fares</div>

    <script>
        const canvas = document.getElementById('heartCanvas');
        const ctx = canvas.getContext('2d');

        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        const width = canvas.width;
        const height = canvas.height;

        function heartX(t) {
            return 15 * Math.pow(Math.sin(t), 3);
        }

        function heartY(t) {
            return -(12 * Math.cos(t) - 5 * Math.cos(2 * t) - 2 * Math.cos(3 * t) - Math.cos(4 * t));
        }

        let i = 0;
        const scale = 15; 

        function draw() {
            if (i > 300) return; 

            ctx.strokeStyle = "red"; // القلب سيظل أحمر ليعطي تبايناً جميلاً مع النصوص الوردي
            ctx.lineWidth = 1;

            const centerX = width / 2;
            const centerY = height / 2;

            ctx.beginPath();
            ctx.moveTo(centerX, centerY);

            const x = centerX + heartX(i) * scale;
            const y = centerY + heartY(i) * scale;

            ctx.lineTo(x, y);
            ctx.stroke();

            i += 0.1; 
            requestAnimationFrame(draw); 
        }

        draw();

        // إعادة ضبط الحجم عند تغيير حجم النافذة
        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });
    </script>
</body>
</html>
