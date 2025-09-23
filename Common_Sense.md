- `sudo apt-get update`
  - 패키지 목록(인덱스)을 최신으로 갱신하는 명령어
  - 이걸 먼저 해야 `python3-venv` 같은 패키지를 정상 위치에서 최신 메타데이터로 찾을 수 있음
  - 오래된 캐시 때문에 **"패키지 못 찾음/404/Hash Sum mismatch"** 같은 오류를 예방 가능
  - 목록만 갱신하는 방식
  
- Git Repo 작명법
  - **kebab-case**(소문자-하이픈) 권장: `project-name`, `data-pipeline`
  - **짧고 구체적으로**: 제품/도메인 + 목적/역할 + (선택)기술·범위

- `git config --global init.defaultBranch`
  - 앞으로 새로 `git init` 하는 로컬 저장소의 기본 브렌치 이름을 `master` 대신 `main`으로 만들라는 설정

- GitHub Repo 연동 시 SSH 키를 쓰는 이유
  - 비밀번호 없이 안전한 인증: 공개키/개인키 방식이라 계정 비번을 저장/전송하지 않음
  - 토큰 유출 리스크 ↓: 브라우저에서 만든 PAT(개인 액세스 토큰) 대신 키파일+에이전트로 인증.
  - 자동화에 유리: CI/CD, 서버(EC2/WSL)에서 **비대화식**으로 git pull/push 가능.
  - 멀티 기기 관리 쉬움: PC/노트북/WSL마다 키를 별도로 등록해 접근 통제.
  - 중간자 공격 방지 도움: 호스트 키 검증(known_hosts)으로 서버 진위를 확인.

- `git push -u origin main`
  - `-u` 는 `--set-upstream`의 약자. 현재 로컬 브랜치(여기선 `main`)를 원격 브랜치(`origin/main`)와 연결해서, 다음부터는 그냥 `git push` / `git pull`만 쳐도 대상이 자동으로 그 브랜치가 되도록 설정
  - 첫 푸시 때 `git push -u origin main` → **업스트림(추적) 브랜치** 설정
  - 이후: `git push`, `git pull` 만으로 OK