# Claude MCP 및 프로젝트 지식 통합 문서

## 1. MCP 도구 목록 (claude_desktop_config.json 기준)

### 사용 가능한 도구들
- **terminal**: npx @wonderwhy-er/desktop-commander
- **filesystem**: npx @modelcontextprotocol/server-filesystem (경로: C:\withClaude)
- **braveSearch**: BRAVE_API_KEY 포함
- **github**: GITHUB_PERSONAL_ACCESS_TOKEN 포함
- **playwright**: 웹 브라우저 자동화
- **googleSearch**: 구글 검색 기능

## 2. 터미널 명령 예시 (Claude 호출 형식)

### 기본 명령어
```json
{ "tool": "terminal", "parameters": { "cmd": "python --version" } }
{ "tool": "terminal", "parameters": { "cmd": "pip install requests" } }
{ "tool": "terminal", "parameters": { "cmd": "git clone https://github.com/user/repo.git" } }
```

### Git 관련 명령어
```json
{ "tool": "terminal", "parameters": { "cmd": "git init" } }
{ "tool": "terminal", "parameters": { "cmd": "git add ." } }
{ "tool": "terminal", "parameters": { "cmd": "git commit -m 'Initial commit'" } }
{ "tool": "terminal", "parameters": { "cmd": "git remote add origin https://github.com/DOBECOMPUTING/withClaude.git" } }
{ "tool": "terminal", "parameters": { "cmd": "git push -u origin main" } }
```

## 3. 부하 테스트 도구 예시

### 사용 가능한 도구들
- **ab** (Apache Bench)
- **wrk** (Modern HTTP benchmarking tool)
- **siege** (HTTP load testing)
- **locust** (Python-based load testing)
- **k6** (JavaScript-based load testing)
- **hey** (HTTP load generator)

### 예시 명령어
```json
{ "tool": "terminal", "parameters": { "cmd": "locust -f locustfile.py" } }
{ "tool": "terminal", "parameters": { "cmd": "ab -n 1000 -c 10 http://localhost:8000/" } }
{ "tool": "terminal", "parameters": { "cmd": "wrk -t12 -c400 -d30s http://localhost:8000/" } }
```

## 4. 파일 작성 규칙

### 분할 규칙
- 긴 파일은 2~3개로 분할 (각 파일 18KB 이하)
- 예: `cooling_ui_main_part1.py`, `cooling_ui_main_part2.py`

### 기록 규칙
- 작업 시마다 project_plan.md에 반드시 기록
- 작업 종료 후 토큰 사용량과 남은 토큰 사용량 표시

## 5. 연구 및 검증 지침

### 분석 기준
- 유사 프로그램 최소 10개 이상 분석
- 불명확하거나 의심스러운 내용은 반드시 사용자에게 확인
- 교차 검증 기반 심층 분석 필요

### 검증 프로세스
1. 다양한 소스에서 정보 수집
2. 신뢰성 있는 자료 우선순위 적용
3. 상호 교차 검증 실시
4. 의심스러운 부분은 사용자와 확인

## 6. Cooling Rack 기술 사양

### 온도 제어 사양
- 온도 범위: -20.0°C ~ 200.0°C (섭씨) / -5°F ~ 400°F (화씨)
- 온도 편차: 0.1 ~ 25.0°C / 1 ~ 100°F
- 통신 프로토콜: RS485 (Modbus RTU)
- 통신 속도: 1200/2400/4800/9600/19200 bps

### 제어 기능
- COOL/HEAT 모드 선택
- 온도 보정: -10.0 ~ 10.0°C / -20 ~ 20°F
- 출력 지연 시간: 0.00 ~ 60.00분
- 통신 주소: 1 ~ 99번

## 7. 프로젝트 제약 조건

### 확장성 요구사항
- 최대 500대의 Cooling Rack 동시 연동 고려
- 백엔드 서버 부하 최소화 필요
- 운영 안정성 및 신뢰성 확보 필수

### 장애 대응
- 센서 장애 대응
- 통신 장애 대응
- 제어 장애 대응
- UI 장애 대응
