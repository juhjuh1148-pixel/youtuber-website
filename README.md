[index.html](https://github.com/user-attachments/files/27988146/index.html)
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>유튜버 종합 리포트 📺 - 인식부터 성공까지</title>
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --yt-red: #ff0000;
      --yt-dark: #282828;
      --bg: #f9f9f9;
      --text: #222;
      --muted: #666;
    }

    body {
      font-family: "Noto Sans KR", -apple-system, BlinkMacSystemFont, sans-serif;
      background: var(--bg);
      color: var(--text);
      line-height: 1.7;
    }

    /* 히어로 */
    .hero {
      background: linear-gradient(135deg, #1a1a1a 0%, #ff0000 100%);
      color: white;
      padding: 80px 20px 100px;
      text-align: center;
      position: relative;
      overflow: hidden;
    }

    .hero::before {
      content: "▶";
      position: absolute;
      font-size: 30em;
      opacity: 0.05;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }

    .hero-content { position: relative; z-index: 1; }

    .hero .badge {
      display: inline-block;
      background: rgba(255,255,255,0.2);
      padding: 6px 18px;
      border-radius: 20px;
      font-size: 0.9em;
      margin-bottom: 16px;
      backdrop-filter: blur(10px);
    }

    .hero h1 {
      font-size: clamp(2em, 5vw, 3.5em);
      font-weight: 900;
      margin-bottom: 12px;
      letter-spacing: -1.5px;
    }

    .hero p {
      font-size: 1.2em;
      opacity: 0.95;
      max-width: 600px;
      margin: 0 auto;
    }

    /* 컨테이너 */
    .container {
      max-width: 900px;
      margin: -50px auto 60px;
      padding: 0 20px;
      position: relative;
      z-index: 2;
    }

    /* 통계 카드 (히어로 아래 떠있는) */
    .stat-cards {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
      gap: 16px;
      margin-bottom: 40px;
    }

    .stat-card {
      background: white;
      border-radius: 16px;
      padding: 24px;
      text-align: center;
      box-shadow: 0 10px 30px rgba(0,0,0,0.08);
    }

    .stat-card .number {
      font-size: 2.5em;
      font-weight: 900;
      color: var(--yt-red);
      line-height: 1;
      margin-bottom: 6px;
    }

    .stat-card .label {
      color: var(--muted);
      font-size: 0.9em;
      font-weight: 500;
    }

    /* 섹션 */
    section.block {
      background: white;
      border-radius: 20px;
      padding: 40px 38px;
      margin-bottom: 24px;
      box-shadow: 0 4px 20px rgba(0,0,0,0.04);
    }

    .section-tag {
      display: inline-block;
      background: var(--yt-red);
      color: white;
      padding: 4px 14px;
      border-radius: 20px;
      font-size: 0.8em;
      font-weight: 700;
      margin-bottom: 12px;
      letter-spacing: 0.5px;
    }

    section h2 {
      font-size: 1.8em;
      font-weight: 900;
      margin-bottom: 8px;
      color: var(--yt-dark);
      letter-spacing: -0.5px;
    }

    section .lead {
      color: var(--muted);
      margin-bottom: 24px;
      font-size: 1.05em;
    }

    section p { margin-bottom: 14px; }

    section strong { color: var(--yt-dark); }

    /* Then vs Now 비교 */
    .comparison {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 20px;
      margin-top: 20px;
    }

    .compare-card {
      padding: 24px;
      border-radius: 14px;
    }

    .compare-card.before {
      background: #fafafa;
      border: 2px solid #e0e0e0;
    }

    .compare-card.after {
      background: linear-gradient(135deg, #fff5f5, #ffe8e8);
      border: 2px solid #ff0000;
    }

    .compare-card h3 {
      font-size: 1.1em;
      margin-bottom: 14px;
      color: var(--yt-dark);
    }

    .compare-card .icon {
      font-size: 2em;
      margin-bottom: 8px;
    }

    .compare-card ul {
      list-style: none;
      padding: 0;
    }

    .compare-card ul li {
      padding: 6px 0 6px 22px;
      position: relative;
      font-size: 0.95em;
      color: #444;
    }

    .compare-card.before ul li::before {
      content: "✕";
      color: #999;
      position: absolute;
      left: 0;
      font-weight: 700;
    }

    .compare-card.after ul li::before {
      content: "✓";
      color: var(--yt-red);
      position: absolute;
      left: 0;
      font-weight: 700;
    }

    /* 부모님 인식 박스 */
    .parent-quote {
      background: linear-gradient(135deg, #fff8e1, #fff3cd);
      border-left: 5px solid #f9a825;
      padding: 18px 24px;
      margin: 14px 0;
      border-radius: 8px;
      font-style: italic;
      color: #5d4e1f;
    }

    .parent-quote .speaker {
      font-style: normal;
      font-weight: 700;
      color: #b8860b;
      font-size: 0.9em;
      margin-top: 8px;
      display: block;
    }

    /* 성공 확률 - 프로그레스 바 */
    .success-stats {
      margin: 24px 0;
    }

    .success-row {
      margin-bottom: 18px;
    }

    .success-label {
      display: flex;
      justify-content: space-between;
      margin-bottom: 6px;
      font-size: 0.95em;
    }

    .success-label .name { font-weight: 600; }
    .success-label .value { color: var(--yt-red); font-weight: 700; }

    .success-bar-bg {
      height: 14px;
      background: #f0f0f0;
      border-radius: 50px;
      overflow: hidden;
    }

    .success-bar {
      height: 100%;
      background: linear-gradient(90deg, #ff5722, #ff0000);
      border-radius: 50px;
      transition: width 1s ease;
    }

    /* 성공 비결 카드 */
    .tips-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 16px;
      margin-top: 20px;
    }

    .tip-card {
      background: #fafafa;
      border-radius: 12px;
      padding: 20px;
      border-top: 4px solid var(--yt-red);
      transition: transform 0.2s, box-shadow 0.2s;
    }

    .tip-card:hover {
      transform: translateY(-4px);
      box-shadow: 0 8px 24px rgba(0,0,0,0.08);
    }

    .tip-card .tip-number {
      font-size: 0.85em;
      color: var(--yt-red);
      font-weight: 800;
      letter-spacing: 1px;
      margin-bottom: 6px;
    }

    .tip-card h4 {
      font-size: 1.1em;
      margin-bottom: 8px;
      color: var(--yt-dark);
    }

    .tip-card p {
      font-size: 0.92em;
      color: #555;
      margin: 0;
    }

    /* 연령대 탭 */
    .age-tabs {
      display: flex;
      gap: 8px;
      margin: 20px 0 24px;
      flex-wrap: wrap;
    }

    .age-tab {
      flex: 1;
      min-width: 80px;
      padding: 12px 18px;
      background: #f0f0f0;
      border: none;
      border-radius: 12px;
      cursor: pointer;
      font-weight: 700;
      font-size: 0.95em;
      color: var(--muted);
      transition: all 0.2s;
    }

    .age-tab.active {
      background: var(--yt-red);
      color: white;
    }

    .age-tab:hover:not(.active) {
      background: #e0e0e0;
    }

    .age-panel {
      display: none;
      animation: fadeIn 0.4s;
    }

    .age-panel.active { display: block; }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .youtuber-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
      gap: 14px;
      margin-top: 16px;
    }

    .youtuber-card {
      background: #fafafa;
      border-radius: 10px;
      padding: 16px;
      text-align: center;
      border: 1px solid #eee;
      transition: transform 0.2s, border-color 0.2s;
    }

    .youtuber-card:hover {
      transform: translateY(-3px);
      border-color: var(--yt-red);
    }

    .youtuber-card .category {
      font-size: 0.75em;
      color: var(--yt-red);
      font-weight: 700;
      letter-spacing: 0.5px;
      margin-bottom: 6px;
    }

    .youtuber-card .name {
      font-size: 1em;
      font-weight: 700;
      color: var(--yt-dark);
      margin-bottom: 4px;
    }

    .youtuber-card .desc {
      font-size: 0.82em;
      color: #777;
    }

    /* 결론 박스 */
    .conclusion {
      background: linear-gradient(135deg, #1a1a1a, #ff0000);
      color: white;
      border-radius: 20px;
      padding: 40px;
      text-align: center;
      margin-bottom: 24px;
    }

    .conclusion h2 {
      color: white;
      margin-bottom: 12px;
    }

    .conclusion p {
      opacity: 0.95;
      max-width: 600px;
      margin: 0 auto 12px;
    }

    /* 푸터 */
    footer {
      text-align: center;
      color: #999;
      font-size: 0.85em;
      padding: 20px;
    }

    @media (max-width: 700px) {
      section.block { padding: 28px 22px; }
      .comparison { grid-template-columns: 1fr; }
      .hero { padding: 60px 20px 80px; }
    }
  </style>
</head>
<body>

  <!-- 히어로 -->
  <header class="hero">
    <div class="hero-content">
      <span class="badge">📺 종합 리포트</span>
      <h1>유튜버, 직업이 되다</h1>
      <p>인식 변화부터 성공 확률, 세대별 트렌드까지 한눈에 보는 한국 유튜브 생태계</p>
    </div>
  </header>

  <div class="container">

    <!-- 통계 카드 -->
    <div class="stat-cards">
      <div class="stat-card">
        <div class="number">1,300만+</div>
        <div class="label">국내 유튜브 채널 수<br>(추정)</div>
      </div>
      <div class="stat-card">
        <div class="number">TOP 3</div>
        <div class="label">초등학생<br>장래희망 순위</div>
      </div>
      <div class="stat-card">
        <div class="number">&lt; 1%</div>
        <div class="label">실버 버튼<br>(구독자 10만↑)</div>
      </div>
      <div class="stat-card">
        <div class="number">95%+</div>
        <div class="label">한국인 유튜브<br>이용률</div>
      </div>
    </div>

    <!-- 섹션 1: 사회 인식 -->
    <section class="block">
      <span class="section-tag">SECTION 01</span>
      <h2>📱 유튜버에 대한 사회의 인식</h2>
      <p class="lead">"백수 아니야?"에서 "전문 크리에이터"로 — 10년 사이 가장 극적으로 변한 직업 인식</p>

      <p>
        2010년대 초반만 해도 "유튜브 한다"고 하면 의심의 눈초리를 받기 일쑤였다.
        하지만 지금은 <strong>초등학생 장래희망 1~3위</strong>에 빠지지 않을 만큼 인식이 달라졌다.
        몇몇 톱 유튜버는 연 수십억대 수익을 공개하며 <strong>"진짜 직업"</strong>으로 자리 잡았다.
      </p>

      <div class="comparison">
        <div class="compare-card before">
          <div class="icon">🕰️</div>
          <h3>10년 전 인식</h3>
          <ul>
            <li>"백수 아니야?"라는 의심</li>
            <li>취업 못 한 사람의 도피처</li>
            <li>수익이 진짜냐는 의문</li>
            <li>주변에서 말리는 분위기</li>
            <li>직업이라기보단 취미</li>
          </ul>
        </div>
        <div class="compare-card after">
          <div class="icon">🚀</div>
          <h3>지금의 인식</h3>
          <ul>
            <li>정식 직업으로 인정</li>
            <li>학교 진로 수업에도 등장</li>
            <li>대기업 마케팅 협업 활발</li>
            <li>크리에이터 전문 학원 등장</li>
            <li>세금 신고 등 제도권 편입</li>
          </ul>
        </div>
      </div>

      <p style="margin-top: 20px;">
        다만 부정적 시선도 여전하다. <strong>사이버 렉카, 자극적 콘텐츠, 뒷광고 논란</strong> 같은
        문제로 "신뢰할 수 없는 직업"이라는 시선도 일부 존재한다. 인식이 양극화되어 있다는 것이 현실.
      </p>
    </section>

    <!-- 섹션 2: 부모님 인식 -->
    <section class="block">
      <span class="section-tag">SECTION 02</span>
      <h2>👨‍👩‍👧 부모님 세대의 인식</h2>
      <p class="lead">"안정적인 직업"을 중시하는 부모 세대에게 유튜버는 여전히 어려운 선택</p>

      <p>
        대부분의 부모님은 <strong>공무원, 대기업, 전문직</strong>처럼 안정적인 수입이 보장되는
        직업을 선호한다. 자녀가 "유튜버 하겠다"고 하면 첫 반응은 보통 이렇다:
      </p>

      <div class="parent-quote">
        "그게 돈이 돼? 안정적이지도 않잖아. 일단 취업부터 하고 부업으로 해."
        <span class="speaker">— 가장 흔한 부모님 반응</span>
      </div>

      <div class="parent-quote">
        "10년 뒤에도 그게 직업이라고 할 수 있을까?"
        <span class="speaker">— 미래에 대한 우려</span>
      </div>

      <p style="margin-top: 18px;"><strong>부모님 인식이 바뀌는 순간들:</strong></p>
      <ul style="padding-left: 24px; margin-top: 8px;">
        <li><strong>실제 수익이 검증될 때</strong> — 첫 정산금, 광고 협찬 등이 통장에 찍히는 순간</li>
        <li><strong>주변 또래 부모의 자녀가 성공했을 때</strong> — "○○네 아들은…" 효과</li>
        <li><strong>방송이나 매체에 출연했을 때</strong> — 공중파 인정 = 직업 인정</li>
        <li><strong>꾸준한 활동을 1~2년 이어갔을 때</strong> — "취미가 아니구나" 인식 전환</li>
      </ul>

      <p style="margin-top: 14px;">
        반대로 <strong>젊은 부모(30~40대)</strong>는 자녀가 유튜브를 한다고 하면
        오히려 응원하는 비율이 점점 늘고 있다. 본인들도 유튜브를 일상적으로 시청하는 세대라
        가능성을 더 잘 알기 때문.
      </p>
    </section>

    <!-- 섹션 3: 성공 확률 -->
    <section class="block">
      <span class="section-tag">SECTION 03</span>
      <h2>📊 유튜버 성공 확률</h2>
      <p class="lead">냉정하게 보면 "성공"은 정말 어렵다. 숫자로 살펴보자</p>

      <p>
        한국에 등록된 유튜브 채널은 <strong>약 1,300만 개 이상</strong>으로 추정된다.
        하지만 의미 있는 수익을 내는 채널은 그중 극히 일부.
      </p>

      <div class="success-stats">
        <div class="success-row">
          <div class="success-label">
            <span class="name">📺 채널 개설</span>
            <span class="value">누구나 가능</span>
          </div>
          <div class="success-bar-bg"><div class="success-bar" style="width: 100%;"></div></div>
        </div>
        <div class="success-row">
          <div class="success-label">
            <span class="name">🥉 구독자 1,000명 + 수익화 조건</span>
            <span class="value">약 5~10%</span>
          </div>
          <div class="success-bar-bg"><div class="success-bar" style="width: 8%;"></div></div>
        </div>
        <div class="success-row">
          <div class="success-label">
            <span class="name">🥈 구독자 1만 (만 단위 채널)</span>
            <span class="value">약 1~2%</span>
          </div>
          <div class="success-bar-bg"><div class="success-bar" style="width: 2%;"></div></div>
        </div>
        <div class="success-row">
          <div class="success-label">
            <span class="name">🥇 구독자 10만 (실버 버튼)</span>
            <span class="value">약 0.5~1%</span>
          </div>
          <div class="success-bar-bg"><div class="success-bar" style="width: 1%;"></div></div>
        </div>
        <div class="success-row">
          <div class="success-label">
            <span class="name">💎 구독자 100만 (골드 버튼)</span>
            <span class="value">약 0.01%</span>
          </div>
          <div class="success-bar-bg"><div class="success-bar" style="width: 0.5%;"></div></div>
        </div>
      </div>

      <p>
        <strong>전업으로 먹고살 수준</strong>(월 300만원 이상)까지 가는 채널은
        보통 <strong>구독자 5만~10만 이상</strong>일 때 가능하다.
        즉, 통계적으로 보면 <strong>유튜브로 전업하는 데 성공할 확률은 약 1% 내외</strong>로 추정된다.
      </p>

      <p>
        반대로 말하면 <strong>꾸준히 1~2년만 해도 상위권에 들 수 있다</strong>는 의미이기도 하다.
        대부분의 채널이 6개월 안에 업로드를 멈추기 때문에, 꾸준함만으로도 차별화가 가능하다.
      </p>
    </section>

    <!-- 섹션 4: 성공 비결 -->
    <section class="block">
      <span class="section-tag">SECTION 04</span>
      <h2>🔑 성공하려면 어떻게 해야 할까?</h2>
      <p class="lead">실제 성공한 유튜버들이 공통적으로 강조하는 요소들</p>

      <div class="tips-grid">
        <div class="tip-card">
          <div class="tip-number">TIP 01</div>
          <h4>🎯 명확한 니치(주제) 잡기</h4>
          <p>"브이로그"는 너무 넓다. "30대 직장인 자취 브이로그"처럼 좁고 명확하게.</p>
        </div>
        <div class="tip-card">
          <div class="tip-number">TIP 02</div>
          <h4>⏰ 꾸준한 업로드</h4>
          <p>주 1~2회 이상, 최소 1년 이상 끊지 않고 올리기. 70%는 여기서 떨어져 나간다.</p>
        </div>
        <div class="tip-card">
          <div class="tip-number">TIP 03</div>
          <h4>🖼️ 썸네일 & 제목이 90%</h4>
          <p>아무리 좋은 콘텐츠도 클릭이 없으면 죽는다. A/B 테스트 필수.</p>
        </div>
        <div class="tip-card">
          <div class="tip-number">TIP 04</div>
          <h4>⏱️ 시청 지속시간이 핵심</h4>
          <p>유튜브 알고리즘은 "끝까지 본 영상"을 좋아한다. 초반 30초가 승부처.</p>
        </div>
        <div class="tip-card">
          <div class="tip-number">TIP 05</div>
          <h4>📱 숏폼도 함께 운영</h4>
          <p>유튜브 Shorts, 인스타 릴스, 틱톡으로 유입 채널 다각화.</p>
        </div>
        <div class="tip-card">
          <div class="tip-number">TIP 06</div>
          <h4>💬 시청자와 소통</h4>
          <p>댓글 답변, 라이브 방송, 커뮤니티 글로 팬덤을 만들기.</p>
        </div>
        <div class="tip-card">
          <div class="tip-number">TIP 07</div>
          <h4>🔥 트렌드 빠르게 캐치</h4>
          <p>화제 키워드가 나오면 24시간 안에 콘텐츠로. 알고리즘 추천 받기.</p>
        </div>
        <div class="tip-card">
          <div class="tip-number">TIP 08</div>
          <h4>🤖 AI 도구 적극 활용</h4>
          <p>ChatGPT로 기획, 캡션 자동 생성, AI 편집 도구로 시간 단축.</p>
        </div>
        <div class="tip-card">
          <div class="tip-number">TIP 09</div>
          <h4>📈 분석 데이터 보기</h4>
          <p>유튜브 스튜디오의 시청자 이탈 지점, 노출 클릭률(CTR)을 매번 확인.</p>
        </div>
        <div class="tip-card">
          <div class="tip-number">TIP 10</div>
          <h4>💎 본인만의 색깔</h4>
          <p>따라하는 채널은 오래 못 간다. "이 사람이라야 보는 이유"를 만들기.</p>
        </div>
      </div>
    </section>

    <!-- 섹션 5: 연령대별 인기 유튜버 -->
    <section class="block">
      <span class="section-tag">SECTION 05</span>
      <h2>🎬 연령대별 인기 유튜버</h2>
      <p class="lead">탭을 눌러서 각 세대가 어떤 채널을 좋아하는지 확인해보세요</p>

      <div class="age-tabs">
        <button class="age-tab active" onclick="showAge('teen', this)">10대</button>
        <button class="age-tab" onclick="showAge('twenty', this)">20대</button>
        <button class="age-tab" onclick="showAge('thirty', this)">30대</button>
        <button class="age-tab" onclick="showAge('forty', this)">40대 이상</button>
      </div>

      <!-- 10대 -->
      <div class="age-panel active" id="age-teen">
        <p><strong>키워드: 게임, 숏폼, 챌린지, 학습, 친근한 캐릭터</strong></p>
        <p style="color: #666; font-size: 0.95em;">
          짧고 자극적인 콘텐츠를 선호하며, 유튜브 Shorts와 틱톡식 영상에 익숙하다.
          게임 실황·먹방·학습 채널이 골고루 인기.
        </p>
        <div class="youtuber-grid">
          <div class="youtuber-card">
            <div class="category">🎮 게임</div>
            <div class="name">우왁굳 · 풍월량</div>
            <div class="desc">게임 실황 / 토크</div>
          </div>
          <div class="youtuber-card">
            <div class="category">🍜 먹방</div>
            <div class="name">햄지 · 입짧은햇님</div>
            <div class="desc">대식가 먹방</div>
          </div>
          <div class="youtuber-card">
            <div class="category">🎤 엔터/예능</div>
            <div class="name">침착맨 · 곽튜브</div>
            <div class="desc">토크 / 여행 예능</div>
          </div>
          <div class="youtuber-card">
            <div class="category">📚 학습</div>
            <div class="name">미미미누</div>
            <div class="desc">수능·입시 콘텐츠</div>
          </div>
          <div class="youtuber-card">
            <div class="category">🎭 캐릭터</div>
            <div class="name">총몇명 · 흔한남매</div>
            <div class="desc">애니/콩트 채널</div>
          </div>
          <div class="youtuber-card">
            <div class="category">⚡ 숏폼</div>
            <div class="name">댄스/챌린지 크리에이터</div>
            <div class="desc">틱톡·릴스 스타</div>
          </div>
        </div>
      </div>

      <!-- 20대 -->
      <div class="age-panel" id="age-twenty">
        <p><strong>키워드: 자기계발, 일상, 코미디, 여행, 재테크</strong></p>
        <p style="color: #666; font-size: 0.95em;">
          취업·연애·자취 등 자신과 비슷한 또래의 일상을 다루는 채널과,
          본격적으로 미래를 고민하는 자기계발 채널이 강세.
        </p>
        <div class="youtuber-grid">
          <div class="youtuber-card">
            <div class="category">📈 경제/재테크</div>
            <div class="name">슈카월드</div>
            <div class="desc">경제 트렌드 토크</div>
          </div>
          <div class="youtuber-card">
            <div class="category">😂 코미디</div>
            <div class="name">피식대학 · 침착맨</div>
            <div class="desc">스케치 코미디</div>
          </div>
          <div class="youtuber-card">
            <div class="category">🌍 여행</div>
            <div class="name">곽튜브 · 빠니보틀</div>
            <div class="desc">날 것의 여행 브이로그</div>
          </div>
          <div class="youtuber-card">
            <div class="category">💼 자기계발</div>
            <div class="name">신사임당 · 부읽남</div>
            <div class="desc">부업·자산관리</div>
          </div>
          <div class="youtuber-card">
            <div class="category">🏠 일상/브이로그</div>
            <div class="name">자취·연애 브이로거</div>
            <div class="desc">또래 공감 콘텐츠</div>
          </div>
          <div class="youtuber-card">
            <div class="category">💄 뷰티/패션</div>
            <div class="name">리뷰·하울 채널</div>
            <div class="desc">쇼핑 가이드</div>
          </div>
        </div>
      </div>

      <!-- 30대 -->
      <div class="age-panel" id="age-thirty">
        <p><strong>키워드: 재테크, 부동산, 육아, 자기계발, 시사</strong></p>
        <p style="color: #666; font-size: 0.95em;">
          결혼·내 집 마련·육아 등 인생의 큰 이벤트가 몰리는 시기.
          돈, 부동산, 자녀교육 콘텐츠가 강세이며 시사 채널도 즐겨본다.
        </p>
        <div class="youtuber-grid">
          <div class="youtuber-card">
            <div class="category">🏠 부동산</div>
            <div class="name">부읽남 · 월급쟁이부자들</div>
            <div class="desc">실전 부동산 정보</div>
          </div>
          <div class="youtuber-card">
            <div class="category">💰 재테크</div>
            <div class="name">슈카월드 · 김작가TV</div>
            <div class="desc">투자/경제 분석</div>
          </div>
          <div class="youtuber-card">
            <div class="category">🍼 육아</div>
            <div class="name">육아 브이로거</div>
            <div class="desc">육아 정보·일상</div>
          </div>
          <div class="youtuber-card">
            <div class="category">📚 자기계발</div>
            <div class="name">김미경 · 김창옥</div>
            <div class="desc">강연 / 인생 멘토링</div>
          </div>
          <div class="youtuber-card">
            <div class="category">📰 시사</div>
            <div class="name">시사 채널들</div>
            <div class="desc">뉴스·정치 해설</div>
          </div>
          <div class="youtuber-card">
            <div class="category">🏕️ 취미</div>
            <div class="name">캠핑·낚시·골프</div>
            <div class="desc">레저 콘텐츠</div>
          </div>
        </div>
      </div>

      <!-- 40대+ -->
      <div class="age-panel" id="age-forty">
        <p><strong>키워드: 건강, 가요/트로트, 시사, 요리, 종교</strong></p>
        <p style="color: #666; font-size: 0.95em;">
          유튜브 이용 시간이 가장 긴 세대.
          트로트·건강·시사·요리가 압도적으로 강세.
        </p>
        <div class="youtuber-grid">
          <div class="youtuber-card">
            <div class="category">🎤 트로트/가요</div>
            <div class="name">임영웅 · 트로트 채널</div>
            <div class="desc">팬덤 콘텐츠</div>
          </div>
          <div class="youtuber-card">
            <div class="category">💊 건강</div>
            <div class="name">건강의학 채널들</div>
            <div class="desc">의사·약사 정보</div>
          </div>
          <div class="youtuber-card">
            <div class="category">📺 시사/정치</div>
            <div class="name">정치 시사 채널</div>
            <div class="desc">강한 팬층</div>
          </div>
          <div class="youtuber-card">
            <div class="category">🍳 요리</div>
            <div class="name">백종원의 요리비책</div>
            <div class="desc">실용 레시피</div>
          </div>
          <div class="youtuber-card">
            <div class="category">🙏 종교</div>
            <div class="name">설교/명상 채널</div>
            <div class="desc">신앙 콘텐츠</div>
          </div>
          <div class="youtuber-card">
            <div class="category">📖 다큐</div>
            <div class="name">역사·교양</div>
            <div class="desc">긴 호흡의 콘텐츠</div>
          </div>
        </div>
      </div>
    </section>

    <!-- 결론 -->
    <div class="conclusion">
      <h2>📌 정리하자면</h2>
      <p>
        <strong>유튜버는 더 이상 "도피처"가 아니라 "정식 직업"</strong>입니다.
        다만 성공 확률은 <strong>약 1% 내외</strong>로 매우 낮고,
        대부분의 채널이 1년을 못 버틴다는 현실도 직시해야 합니다.
      </p>
      <p>
        <strong>꾸준함 + 명확한 주제 + 시청자 분석 + 트렌드 캐치</strong>가 핵심이며,
        각 세대마다 좋아하는 콘텐츠가 완전히 다르니
        <strong>"누구를 위한 채널인가"</strong>를 가장 먼저 정해야 합니다.
      </p>
      <p style="margin-top: 16px; font-size: 0.95em; opacity: 0.85;">
        🚀 시작이 곧 50%. 일단 첫 영상을 올려보세요!
      </p>
    </div>

  </div>

  <footer>
    <p>※ 본 리포트의 통계는 공개된 자료를 기반으로 한 추정치이며, 실제와 다를 수 있습니다.</p>
    <p style="margin-top: 6px;">© 2026 유튜버 종합 리포트 (샘플 페이지)</p>
  </footer>

  <script>
    function showAge(ageKey, button) {
      document.querySelectorAll(".age-panel").forEach(p => p.classList.remove("active"));
      document.querySelectorAll(".age-tab").forEach(t => t.classList.remove("active"));
      document.getElementById("age-" + ageKey).classList.add("active");
      button.classList.add("active");
    }
  </script>

</body>
</html>
