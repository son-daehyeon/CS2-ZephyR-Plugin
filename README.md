# CS2-ZephyR-Plugin

> ZephyR CS2 서버 플러그인, 스킨·매치·나이프 라운드 등 8개 모듈 (C# · CounterStrikeSharp)

ZephyR는 2024년에 만든 Counter-Strike 2 내전용 커뮤니티 서버다. 이 플러그인은 CS2 전용 서버에 올라가 웹에서 고른 스킨을 적용하고, 가입한 유저만 받으며 내전 진행을 돕는다.

## 주요 기능
- CustomSkin: MongoDB에 저장된 무기 스킨·칼·장갑·에이전트·뮤직 키트를 적용 (`!skin`으로 새로고침)
- ColoredSmoke: 유저가 고른 색으로 연막 표시 (`!smoke`로 켜고 끄기)
- UserManager: 가입된 유저만 접속 허용(관리자 제외), 클랜 태그 `ZephyR` 표시
- MatchManager: 경기 팀 이름 지정, 팀원 자동 배정, 일시정지(`!p`, `!up`), 디스코드 봇에 WebSocket으로 서버 준비·경기 종료 알림, 경기 후 서버 종료
- KnifeRound: 나이프 라운드 승리 팀이 `!ct`·`!t`로 진영 선택
- DamageInfo: 라운드별 준·받은 피해 표시, `!hp`
- C4Timer: 설치된 C4 남은 시간 표시
- WarmupWeapon: 워밍업 중 무기 지급

## 기술 스택
| 영역 | 기술 |
|---|---|
| 언어 | C# (.NET 8) |
| 프레임워크 | CounterStrikeSharp.API 1.0.202, WebSocketSharp |
| 데이터 | MongoDB (MongoDB.Driver 2.23.1) |

## 구조
```
ZephyrPlugin/
  ZephyrPlugin.cs        플러그인 진입점, 모듈 로드
  Module/ZephyrModule.cs 모듈 기반 클래스
  Module/<이름>/         Module·Command·Event·Timer로 나눈 기능 모듈 8개
  Util/                  설정, MongoDB, 로거
```

## 실행
```bash
dotnet build
```
빌드 결과를 CounterStrikeSharp 플러그인 폴더에 넣는다. 플러그인 설정 파일의 `MongoDB` 항목(Hostname, Port, Username, Password, Database)을 채워야 한다.

## 관련 저장소
- [CS2-ZephyR-Server](https://github.com/son-daehyeon/CS2-ZephyR-Server) — 백엔드 API
- [CS2-ZephyR-Client](https://github.com/son-daehyeon/CS2-ZephyR-Client) — 스킨 설정 웹
- [CS2-ZephyR-Bot](https://github.com/son-daehyeon/CS2-ZephyR-Bot) — 디스코드 봇, 가입 연동과 내전 관리

---
2024 · 개인 프로젝트 · 보관됨
