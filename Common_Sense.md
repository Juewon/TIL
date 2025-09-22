- `sudo apt-get update`
  - 패키지 목록(인덱스)을 최신으로 갱신하는 명령어
  - 이걸 먼저 해야 `python3-venv` 같은 패키지를 정상 위치에서 최신 메타데이터로 찾을 수 있음
  - 오래된 캐시 때문에 **"패키지 못 찾음/404/Hash Sum mismatch"** 같은 오류를 예방 가능
  - 목록만 갱신하는 방식
  
- Git Repo 작명법
  - **kebab-case**(소문자-하이픈) 권장: `project-name`, `data-pipeline`
  - **짧고 구체적으로**: 제품/도메인 + 목적/역할 + (선택)기술·범위
 