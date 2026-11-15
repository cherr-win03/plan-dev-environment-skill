# 내 PC 개발 도구와 반복된 함정 (양식)

이 파일을 복사해 `this-machine.md`로 저장하고 자기 PC에 맞게 채운다. 환경을 준비할 때만 읽는다. 아래는 Windows에서 실제로 겪은 예시다.

## 도구 상태 (확인한 날짜를 적는다)

- 있음: 예) Node 24, Python 3.14(`python`), Git Bash, `gh`(로그인됨), ffmpeg
- 없음: 예) `jq`, 전역 `wrangler`(프로젝트의 `npx wrangler`를 쓴다)
- 경로 주의: 예) PATH에 없는 CLI는 전체 경로로 부른다

## 반복된 함정 (예시)

- Python `-I`(격리 모드)는 UTF-8 환경 변수를 무시한다. 한글 출력이 깨지면 `python -I -X utf8`로 실행한다.
- 셸 heredoc이나 `python -c` 안에서 백슬래시가 줄어 Windows 경로가 깨질 수 있다. 백슬래시가 든 스크립트는 파일로 저장한 뒤 실행한다.
- PowerShell 파이프로 네이티브 명령(`git mktree` 등)에 넘기면 줄 끝에 CR이 붙는다. Git Bash `printf`나 node로 넘긴다.
- 브라우저·시험 출력이 워크트리마다 쌓여 디스크를 채운다. 검증이 끝나면 무시된 출력만 골라 지운다.
- 클라우드 동기화 드라이브(Google Drive 등)에서 재귀 검색·전체 해시를 돌리면 파일을 전부 내려받기 시작한다. 하지 않는다.
