# GIT COMMIT CONVENTION
**1. 기본 형식(한 줄만)**
- `<type>(<scope>): <subject>`
- **type**: feat, fix, docs, style, refactor, test, chore, perf, build, ci
- **scope**(선택): 모듈/폴더명(ex. api, web, auth)
- **subject**: 명령형 현재형, 50자 내(설명은 "한다"가 아닌 "~하라" 톤)
    - ex. `feat(api): add dish lookup endpoint`

- **type별 의미 정리**
    - **feat**: 새 기능 추가
      - ex. 검색 필터 추가, 새 API 엔드포인트 생성
    - **fix**: 버그 수정
      - ex. 널 포인터 예외 처리, 잘못된 페이지네이션 고침
    - **docs**: 문서 변경만
      - ex. README 보완, 주석/가이드 업데이트
    - **style**: 의미 없는 코드 스타일 변경(로직은 무변경)
      - ex. 포맷팅, 세미콜론/공백, lint auto-fix
    - **refactor**: 기능 변화 없이 구조 개선
      - ex. 함수 분리, 모듈화, 네이밍 정리
    - **test**: 테스트 추가/수정
      - ex. 단위/통합 테스트 보강, 목(mock) 교체
    - **chore**: 빌드·도구·환경 등 잡무(코드/테스트 미포함)
      - ex. 패키지 업데이트, 스크립트 정리
    - **perf**: 성능 개선(기능 동일, 더 빠름/가벼움)
      - ex. 쿼리 최적화, 렌더링 비용 감소
    - **build**: 빌드 시스템/의존성 변경
      - ex. Webpack/Vite 설정, 의존성 버전 고정
    - **ci**: CI 설정/스크립트 변경
      - ex. GitHub Actions 워크플로 수정, 캐시 전략 변경

**2. 본문/푸터가 있는 형식**
```markdown
<type>(<scope>): <subject> 

<body>
<footer>
```
- **body**: 변경 이유/배경, 설계 선택, 사이드이펙트(72자 줄바꿈 권장)
- **footer**: 이슈/브레이킹/Co-authored 등
  - `BREAKING CHANGE: ...`
  - `Closes #123`, `Refs #456`
  - `Co-authored-by: 이름 <email>`

**예시**
```bash
fix(web): prevent duplicate uploads on slow networks

Use request lock to avoid double-submit when the user clicks twice.
Also debounced the button handler to 500ms.

Closes #274
```

**3. 메시지 작성 팁**
- **명령형**으로: Added(X) → Add(O)
- 제목에 마침표 **X**, 본문에 이유/영향
- 한 커밋 = **한 가지 목적**
- "update", "fix bug" 같은 모호한 표현 금지
- UI/버그/성능 등 사용자 영향을 본문에 명확히 하기

**4. 입력 방법 예시**
- **간단히 한 줄**
    ```bash
    git commit -m "feat(api): add dish lookup endpoint
    ```
- **본문 포함(여러 줄)**
  ```bash
  git commit -m "fix(web): prevent double uploads" \
                -m "Lock request & debounce; closes #274"
  ```
- **에디터로 작성**
  ```bash
  git config --global core.editor "code --wait"  # VS Code
  git commit                                     # 에디터 열림
  ```
- **직전 메시지 수정**
  ```bash
  git commit --amend
  ```
- **서명/공동 기여자**
  ```bash
  git commit -s             # Signed-off-by trailer 추가
  # 본문에:
  # Co-authored-by: Alice <alice@example.com> 
  ```

작게·자주 커밋하고, 제목엔 **무엇**, 본문엔 **왜/어떻게/영향**ㅡ이렇게만 지켜도 코드 리뷰와 이력 추적이 훨씬 쉬워짐