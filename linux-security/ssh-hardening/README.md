# 🔐 SSH Server Hardening — Rocky Linux

## 1. 실습 개요

Rocky Linux 환경에서 SSH 서버의 보안 설정을 변경하고 원격 접속 동작을 검증한 실습입니다.

SSH 기본 설정을 확인하고, 원격 접속 제한 정책을 적용한 뒤 실제 클라이언트에서 접속을 테스트했습니다.

## 2. 실습 환경

| 구분 | 환경 |
|---|---|
| 가상화 | VMware Workstation |
| 운영체제 | Rocky Linux 9.3 |
| 서비스 | OpenSSH Server |
| SSH 포트 | 10022/TCP |
| 설정 파일 | /etc/ssh/sshd_config |

## 3. 주요 보안 설정

| 설정 항목 | 설정값 | 목적 |
|---|---|---|
| Port | 10022 | 실습용 SSH 포트 변경 |
| PermitRootLogin | no | root 직접 로그인 제한 |
| LoginGraceTime | 30 | 인증 대기 시간 제한 |
| MaxAuthTries | 2 | 연결당 인증 시도 횟수 제한 |
| MaxSessions | 10 | 연결당 세션 수 제한 |
| Banner | /etc/ssh/ssh_banner | 접속 전 안내 문구 표시 |

## 4. 실습 및 검증

- 기존 SSH 설정 파일 백업
- SSH 보안 정책 수정
- `sshd -t` 명령으로 설정 문법 검증
- `sshd -T` 명령으로 실제 적용 설정 확인
- 일반 사용자 원격 접속 및 배너 확인
- root 직접 로그인 제한 확인

## 5. 트러블슈팅

`LoginGraceTime`을 변경했지만 적용된 설정에서 기존 값이 출력되는 문제가 발생했습니다.

설정 파일을 확인한 결과, 해당 설정이 주석 처리되어 있었습니다. 주석을 해제한 후 설정을 재검증하여 변경값을 확인했습니다.

**배운 점:** 설정 파일을 수정했다는 사실만으로 정책 적용을 확신할 수 없으며, 실제 적용된 설정과 서비스 동작을 함께 확인해야 합니다.

## 6. 보안 관점

SSH 포트 변경만으로 서버가 안전해지는 것은 아닙니다.

관리자 직접 로그인 제한, 인증 정책, 접근제어, 로그 모니터링 등의 보안 대책을 함께 고려해야 합니다.

## 7. 상세 실습 기록

📖 [Velog — SSH 서버 보안 강화 및 원격 접속 검증 실습](https://velog.io/@sunsuhak2020/Linux-Security-SSH-서버-보안-강화-및-원격-접속-검증-실습)

---

**Build → Secure → Verify → Improve**
