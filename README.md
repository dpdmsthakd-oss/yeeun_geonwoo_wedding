<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>예은 & 건우의 편지</title>
    <style>
        /* (기존 배경, 봉투, 편지 CSS는 그대로 유지) */
        body { background-color: #f5f5f5; display: flex; justify-content: center; align-items: center; height: 100vh; margin: 0; font-family: 'Nanum Myeongjo', serif; }
        .envelope-wrapper { position: relative; cursor: pointer; }
        .envelope { position: relative; width: 300px; height: 200px; background-color: #d1bfa7; border-bottom-left-radius: 10px; border-bottom-right-radius: 10px; z-index: 1; }
        .envelope::before { content: ""; position: absolute; top: 0; z-index: 4; border-top: 110px solid #c2b09a; border-left: 150px solid transparent; border-right: 150px solid transparent; transform-origin: top; transition: transform 0.5s ease-in-out; }
        .envelope-wrapper.open .envelope::before { transform: rotateX(180deg); z-index: 0; }
        .letter { position: absolute; bottom: 10px; left: 10px; width: 280px; height: 180px; background-color: white; padding: 20px; box-sizing: border-box; transition: transform 0.5s ease-in-out; z-index: 2; box-shadow: 0 -5px 15px rgba(0,0,0,0.1); text-align: center; }
        .envelope-wrapper.open .letter { transform: translateY(-120px); height: auto; min-height: 250px; }
        .letter h2 { font-size: 18px; color: #555; }
        .letter p { font-size: 14px; line-height: 1.6; color: #777; }
        

        /* --- 💧 물방울 하트 애니메이션 CSS --- */
        .drop-seal {
            position: absolute;
            top: 40%;
            left: 50%;
            transform: translate(-50%, -50%);
            z-index: 5;
            transition: opacity 0.3s;
        }

        /* 물방울 모양 (떨어지기 전) */
        .water-drop {
            width: 20px;
            height: 20px;
            background-color: #ffb7c5; /* 연한 하트 핑크색 */
            border-radius: 0 50% 50% 50%;
            transform: rotate(45deg);
            animation: drip 1.5s infinite; /* 톡 떨어지는 애니메이션 */
            opacity: 0.8;
        }

        /* 봉투 열릴 때 인장 숨기기 */
        .envelope-wrapper.open .drop-seal {
            opacity: 0;
            pointer-events: none;
        }

        /* [핵심] 떨어지는 애니메이션 정의 */
        @keyframes drip {
            0% { transform: translateY(-100px) scale(0.8) rotate(45deg); opacity: 0; }
            50% { opacity: 1; }
            80% { 
                transform: translateY(0) scale(1) rotate(45deg); /* 봉투에 딱 닿음 */
                border-radius: 0 50% 50% 50%; /* 아직 물방울 모양 */
            }
            100% { 
                transform: translateY(0) scale(1.5) rotate(0deg); /* 퍼지면서 하트 모양으로 변신! */
                border-radius: 50%; /* 하트 기초 모양 */
                background-color: #ff6b81; /* 진한 하트 핑크색 */
                box-shadow: 0 0 10px rgba(255, 107, 129, 0.5);
                opacity: 0; /* 터지면서 사라짐 */
            }
        }

        /* 하트 모양을 만들기 위한 가상 요소 (CSS 하트) */
        .water-drop::before,
        .water-drop::after {
            content: '';
            position: absolute;
            width: 100%;
            height: 100%;
            background-color: inherit;
            border-radius: 50%;
            transition: all 0.5s;
        }
        .water-drop::before { top: -50%; left: 0; }
        .water-drop::after { left: -50%; top: 0; }
        /* ---------------------------------- */

    </style>
</head>
<body>

    <div class="envelope-wrapper" onclick="openEnvelope()">
        
        <div class="drop-seal">
            <div class="water-drop"></div>
        </div>

        <div class="envelope"></div>
        <div class="letter">
            <h2>사랑하는 분들에게</h2>
            <p>
                함께 있을 때 가장 나다워지는<br>
                서로를 만났습니다.<br><br>
                저희의 새로운 시작을<br>
                가장 가까운 곳에서 축복해 주세요.
            </p>
            <p><strong>2026년 10월 어느 날</strong><br>이건우 · 최예은 드림</p>
        </div>
    </div>

    <script>
        // 무한 반복되는 물방울 애니메이션을 봉투 클릭 시 멈추게 하는 스크립트
        function openEnvelope() {
            const wrapper = document.querySelector('.envelope-wrapper');
            const drop = document.querySelector('.water-drop');
            
            wrapper.classList.toggle('open');
            
            // 봉투가 열리면 물방울 애니메이션 멈춤
            if (wrapper.classList.contains('open')) {
                drop.style.animation = 'none';
            } else {
                drop.style.animation = 'drip 1.5s infinite';
            }
        }
    </script>
</body>
</html>
