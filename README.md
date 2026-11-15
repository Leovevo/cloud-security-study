# cloud-security-study

클라우드 보안 엔지니어를 목표로 공부한 내용을 정리한 저장소입니다.
원본 글은 [velog.io/@xjoker7272](https://velog.io/@xjoker7272) 에 작성했고, 이곳으로 옮겨 왔습니다.

## 학습 목적

- 네트워크와 리눅스 기초를 바탕으로 클라우드 인프라를 이해한다
- AWS 환경에서 발생하는 보안 문제의 원인과 대응을 정리한다
- 직접 만들고 배포하면서 겪은 문제와 해결 과정을 기록한다

## 주요 학습 분야

`네트워크` `Linux` `AWS` `클라우드 보안` `DevSecOps` `프로그래밍`

## 카테고리별 글 목록

### 네트워크 (`01-network/`)

| 글 | 작성일 | 원본 |
|---|---|---|
| [2주차- OSI 7 Layer](01-network/01-osi-7-layers.md) | 2026-10-25 | [velog](https://velog.io/@xjoker7272/2%EC%A3%BC%EC%B0%A8-OSI-7-Layer) |
| [3주차-TCP와 UDP의 특징 및 차이점 — 헤더 구조부터 통신 원리까지](01-network/02-tcp-vs-udp.md) | 2026-11-05 | [velog](https://velog.io/@xjoker7272/Network-TCP%EC%99%80-UDP%EC%9D%98-%ED%8A%B9%EC%A7%95-%EB%B0%8F-%EC%B0%A8%EC%9D%B4%EC%A0%90-%ED%97%A4%EB%8D%94-%EA%B5%AC%EC%A1%B0%EB%B6%80%ED%84%B0-%ED%86%B5%EC%8B%A0-%EC%9B%90%EB%A6%AC%EA%B9%8C%EC%A7%80) |
| [4주차-OSI 1~4계층 네트워크 장비 총정리 — 허브, 스위치, 라우터, 로드밸런서](01-network/03-network-devices.md) | 2026-11-15 | [velog](https://velog.io/@xjoker7272/4%EC%A3%BC%EC%B0%A8-OSI-14%EA%B3%84%EC%B8%B5-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-%EC%9E%A5%EB%B9%84-%EC%B4%9D%EC%A0%95%EB%A6%AC-%ED%97%88%EB%B8%8C-%EC%8A%A4%EC%9C%84%EC%B9%98-%EB%9D%BC%EC%9A%B0%ED%84%B0-%EB%A1%9C%EB%93%9C%EB%B0%B8%EB%9F%B0%EC%84%9C) |
| [\[Network\] 계층별 프로토콜의 특징과 차이점 — FTP, SMTP, POP3, IMAP, ICMP](01-network/04-protocols-ftp-email-icmp.md) | 2026-11-16 | - |

### 서버·리눅스 (`02-linux/`)

| 글 | 작성일 | 원본 |
|---|---|---|
| [8주차-nginx,서브도메인,SSL](02-linux/01-nginx-subdomain-ssl.md) | 2026-09-06 | [velog](https://velog.io/@xjoker7272/8%EC%A3%BC%EC%B0%A8-nginx%EC%84%9C%EB%B8%8C%EB%8F%84%EB%A9%94%EC%9D%B8SSL) |

### 클라우드·AWS (`03-aws/`)

| 글 | 작성일 | 원본 |
|---|---|---|
| [4주차-호스팅,클라우드,그리고 Git](03-aws/01-hosting-cloud-git.md) | 2026-08-09 | [velog](https://velog.io/@xjoker7272/4%EC%A3%BC%EC%B0%A8-%ED%98%B8%EC%8A%A4%ED%8C%85%ED%81%B4%EB%9D%BC%EC%9A%B0%EB%93%9C%EA%B7%B8%EB%A6%AC%EA%B3%A0-Git) |
| [10주차-Scale up과 Scale out](03-aws/02-scale-up-vs-scale-out.md) | 2026-09-20 | [velog](https://velog.io/@xjoker7272/10%EC%A3%BC%EC%B0%A8-Scale-up%EA%B3%BC-Scale-out-xyqupg95) |

### 클라우드 보안 (`04-cloud-security/`)

| 글 | 작성일 | 원본 |
|---|---|---|
| [1주차-클라우드는 안전한데 왜 사고가 날까?](04-cloud-security/01-why-cloud-incidents-happen.md) | 2026-10-11 | [velog](https://velog.io/@xjoker7272/1%EC%A3%BC%EC%B0%A8-%ED%81%B4%EB%9D%BC%EC%9A%B0%EB%93%9C%EB%8A%94-%EC%95%88%EC%A0%84%ED%95%9C%EB%8D%B0-%EC%99%9C-%EC%82%AC%EA%B3%A0%EA%B0%80-%EB%82%A0%EA%B9%8C) |

### 프로그래밍 기초 (`05-programming/`)

| 글 | 작성일 | 원본 |
|---|---|---|
| [0주차 과제-기본개념 정리 과제](05-programming/01-basic-concepts.md) | 2026-07-10 | [velog](https://velog.io/@xjoker7272/0%EC%A3%BC%EC%B0%A8-%EA%B8%B0%EB%B3%B8%EA%B0%9C%EB%85%90-%EC%A0%95%EB%A6%AC-%EA%B3%BC%EC%A0%9C) |
| [1주차 과제-CSS/JS 기초](05-programming/02-css-js-basics.md) | 2026-07-19 | [velog](https://velog.io/@xjoker7272/1%EC%A3%BC%EC%B0%A8-%EA%B3%BC%EC%A0%9C-CSSJS-%EA%B8%B0%EC%B4%88) |
| [2주차 과제-SPA/MPA, REACT, 그리고 JSX](05-programming/03-spa-mpa-react-jsx.md) | 2026-07-26 | [velog](https://velog.io/@xjoker7272/2%EC%A3%BC%EC%B0%A8-%EA%B3%BC%EC%A0%9C) |
| [3주차 과제-Next.js vs REACT](05-programming/04-nextjs-vs-react.md) | 2026-08-02 | [velog](https://velog.io/@xjoker7272/3%EC%A3%BC%EC%B0%A8-%EA%B3%BC%EC%A0%9C-Next.js-vs-REACT) |
| [6주차 SPA,MPA 개념 이해하기](05-programming/05-spa-mpa-concepts.md) | 2026-08-23 | [velog](https://velog.io/@xjoker7272/6%EC%A3%BC%EC%B0%A8-SPAMPA-%EA%B0%9C%EB%85%90-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0) |
| [11주차-DB-RDBMS와 NOSQL](05-programming/06-rdbms-vs-nosql.md) | 2026-09-28 | [velog](https://velog.io/@xjoker7272/11%EC%A3%BC%EC%B0%A8-DB-RDBMS%EC%99%80-NOSQL) |

### 프로젝트 (`06-projects/`)

| 글 | 작성일 | 원본 |
|---|---|---|
| [5주차-챗봇 제작, Vercel, 도메인](06-projects/01-chatbot-vercel-domain.md) | 2026-08-17 | [velog](https://velog.io/@xjoker7272/5%EC%A3%BC%EC%B0%A8-%EC%B1%97%EB%B4%87-%EC%A0%9C%EC%9E%91-Vercel-%EB%8F%84%EB%A9%94%EC%9D%B8) |
| [7주차-api 만들기,/sendmessage,챗봇,](06-projects/02-api-sendmessage-chatbot.md) | 2026-08-30 | [velog](https://velog.io/@xjoker7272/7%EC%A3%BC%EC%B0%A8-api-%EB%A7%8C%EB%93%A4%EA%B8%B0sendmessage%EC%B1%97%EB%B4%87) |
| [Pguso/agents-from-scratch](06-projects/03-agents-from-scratch.md) | 2026-09-29 | [velog](https://velog.io/@xjoker7272/Pgusoagents-from-scratch) |

## 최근 추가한 글

- [\[Network\] 계층별 프로토콜의 특징과 차이점 — FTP, SMTP, POP3, IMAP, ICMP](01-network/04-protocols-ftp-email-icmp.md) — 2026-11-16
- [4주차-OSI 1~4계층 네트워크 장비 총정리 — 허브, 스위치, 라우터, 로드밸런서](01-network/03-network-devices.md) — 2026-11-15
- [3주차-TCP와 UDP의 특징 및 차이점 — 헤더 구조부터 통신 원리까지](01-network/02-tcp-vs-udp.md) — 2026-11-05
- [2주차- OSI 7 Layer](01-network/01-osi-7-layers.md) — 2026-10-25
- [1주차-클라우드는 안전한데 왜 사고가 날까?](04-cloud-security/01-why-cloud-incidents-happen.md) — 2026-10-11

---

총 17편 · 최종 갱신 2026-11-16
