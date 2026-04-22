<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>예은 ♥ 건우의 결혼식</title>
    <link href="https://fonts.googleapis.com/css2?family=Nanum+Myeongjo:wght@400;700&display=swap" rel="stylesheet">
    <style>
        body { background-color: #f8f1f1; display: flex; flex-direction: column; align-items: center; min-height: 100vh; margin: 0; font-family: 'Nanum Myeongjo', serif; overflow-x: hidden; }
        .envelope-wrapper { position: relative; cursor: pointer; margin-top: 100px; margin-bottom: 50px; }
        .envelope { position: relative; width: 320px; height: 220px; background-color: #d1bfa7; border-radius: 0 0 10px 10px; z-index: 1; box-shadow: 0 10px 20px rgba(0,0,0,0.1); }
        .envelope::before { content: ""; position: absolute; top: 0; z-index: 4; border-top: 120px solid #c2b09a; border-left: 160px solid transparent; border-right: 160px solid transparent; transform-origin: top; transition: transform 0.6s ease-in-out; }
        .envelope-wrapper.open .envelope::before { transform: rotateX(180deg); z-index: 0; }
        
        /* 편지지 (모든 정보가 담기는 곳) */
        .letter { position: absolute; bottom: 10px; left: 10px; width: 300px; height: 200px; background-color: white; padding: 25px; box-sizing: border-box; transition: transform 0.6s ease-in-out, height 0.6s ease-in-out; z-index: 2; box-shadow: 0 -5px 15px rgba(0,0,0,0.05); overflow: hidden; text-align: center; }
        .envelope-wrapper.open .letter { transform: translateY(-50px); height: auto; min-height: 800px; padding-bottom: 50px; }

        /* 이미지 스타일 */
        .main-img { width: 100%; border-radius: 5px; margin-bottom: 20px; }
        
        /* 섹션 스타일 (달력, 지도 등) */
        .section { margin-top: 30px; border-top: 1px solid #eee; padding-top: 20px; }
        .section-title { font-weight: bold; color: #8d7d66; margin-bottom: 10px; }
        
        /* 계좌번호 스타일 */
        .account-box { background: #f9f9f9; padding: 10px; border-radius: 5px; font-size: 13px; text-align: left; line-height: 1.8; margin-top: 10px; }

        /* 💧 물방울 하트 애니메이션 */
        .drop-seal { position: absolute; top: 40%; left: 50%; transform: translate(-50%, -50%); z-index: 5; }
        .water-drop { width: 20px; height: 20px; background-color: #ffb7c5; border-radius: 0 50% 50% 50%; transform: rotate(45deg); animation: drip 2s infinite; }
        .envelope-wrapper.open .drop-seal { display: none; }
        @keyframes drip {
            0% { transform: translateY(-100px) scale(0.8) rotate(45deg); opacity: 0; }
            50% { opacity: 1; }
            100% { transform: translateY(0) scale(1.5) rotate(0deg); border-radius: 50%; background-color: #ff6b81; opacity: 0; }
        }
        .water-drop::before, .water-drop::after { content: ''; position: absolute; width: 100%; height: 100%; background-color: inherit; border-radius: 50%; }
        .water-drop::before { top: -50%; left: 0; }
        .water-drop::after { left: -50%; top: 0; }
    </style>
</head>
<body>

    <div class="envelope-wrapper" onclick="this.classList.toggle('open')">
        <div class="drop-seal"><div class="water-drop"></div></div>
        <div class="envelope"></div>
        <div class="letter">
            <img src="main.jpg.jpg" alt="우리 사진" class="main-img">
            
            <h2>최예은 ♡ 이건우</h2>
            <p>저희 두 사람이 사랑으로 만나<br>진실한 가약을 맺고자 합니다.</p>

            <div class="section">
                <div class="section-title">WEDDING DAY</div>
                <p>2026년 10월 3일 (토) 오후 12:30</p>
                </div>

            <div class="section">
                <div class="section-title">LOCATION</div>
                <p>한국기독교연합회관웨딩홀</p>
                <div style="background:#eee; height:150px; line-height:150px; color:#aaa;">https://naver.me/FzSifb7D</div>
            </div>

            <div class="section">
                <div class="section-title">마음 전하실 곳</div>
                <div class="account-box">
                    <b>신부측:</b> 국민은행 123-456-789 (최예은)<br>
                    <b>신랑측:</b> 신한은행 987-654-321 (이건우)
                </div>
            </div>
            
            <p style="margin-top:40px; font-size:12px; color:#aaa;">봉투를 다시 누르면 닫힙니다.</p>
        </div>
    </div>

</body>
</html>
