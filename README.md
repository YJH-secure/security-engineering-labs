# 🔐 Security Engineering Labs

**Security & Cloud Engineer in Progress**

Linux와 네트워크를 기반으로 보안·클라우드 엔지니어링을 공부하며, 직접 수행한 실습과 검증 과정을 정리하는 기술 포트폴리오입니다.

> **Build → Secure → Verify → Improve**

## 🎯 About This Repository

보안 설정을 단순히 적용하는 데 그치지 않고, **설정 목적 → 환경 구축 → 동작 검증 → 문제 해결 → 보안 관점 분석** 순서로 학습하고 기록합니다.

현재는 Linux 시스템 보안과 네트워크 보안 실습을 중심으로 공부하고 있으며, 클라우드 인프라·DevSecOps·애플리케이션 보안·보안 아키텍처로 범위를 확장할 계획입니다.

## 🛠️ Technical Focus

| 분야 | 학습·실습 주제 |
| --- | --- |
| Linux & System Security | Rocky Linux, Ubuntu, SSH, PAM, 계정·권한 관리 |
| Network Security & Monitoring | TCP/IP, Snort IDS, Wireshark, 접근제어 |
| Cloud & DevSecOps | AWS 기초, Docker, 컨테이너 네트워크 |
| Application Security | JWT, API 보안, OWASP 기초 |
| Security Architecture | 보안 요구사항, 인프라 구성도, 검증 시나리오 |

위 항목은 **학습 및 관심 분야**이며, 각 기술의 숙련도를 의미하지 않습니다.

## 📚 Published Technical Blog Posts

현재 Velog에 게시한 실습 기록입니다. GitHub용 구성 파일과 검증 자료는 선별·점검 후 순차적으로 추가할 예정입니다.

| 실습 | 핵심 내용 | 기술 블로그 |
| --- | --- | --- |
| SSH Server Hardening | Rocky Linux SSH 포트·인증 정책 설정, 접속 검증, 트러블슈팅 | [Velog 글 보기](https://velog.io/@sunsuhak2020/Linux-Security-SSH-서버-보안-강화-및-원격-접속-검증-실습) |
| Ubuntu PAM Account Security | 계정 잠금 정책, 인증 실패 기록, 초기화 후 재검증 | [Velog 블로그](https://velog.io/@sunsuhak2020) |

## 📁 Planned Repository Structure

```text
security-engineering-labs/
├── README.md
├── linux-security/
│   ├── ssh-hardening/
│   └── ubuntu-pam-faillock/
├── network-security/
│   └── snort-ids/
├── cloud-devsecops/
├── application-security/
└── architecture-projects/
```

위 폴더는 **향후 구성 계획**이며, 아직 모두 생성된 것은 아닙니다.

## 🔎 Documentation Principles

1. **Why** — 기술의 목적과 보안상 필요성을 설명합니다.
2. **Build** — 실습 환경과 적용 과정을 기록합니다.
3. **Verify** — 로그, 명령어 출력, 실제 동작으로 결과를 확인합니다.
4. **Troubleshoot** — 발생한 문제의 원인과 해결 과정을 분석합니다.
5. **Improve** — 한계점과 추가 개선 방향을 정리합니다.

## 🔗 Links

- **Velog:** https://velog.io/@sunsuhak2020
- **GitHub:** https://github.com/YJH-secure/security-engineering-labs

---

*교육용 실습 환경의 공개 가능한 자료만 정리하며, 비밀번호·인증 토큰·민감정보는 업로드하지 않습니다.*
