# 🔐 Ubuntu PAM Account Lockout — pam_faillock

## 1. 실습 개요

Ubuntu 환경에서 PAM(Pluggable Authentication Modules)과 `pam_faillock`을 이용해 계정 잠금 정책을 설정하고 인증 실패 기록을 분석한 실습입니다.

인증 실패 횟수 누적, 추가 인증 거부 현상, 실패 기록 초기화 후 정상 인증을 검증했습니다.

## 2. 실습 환경

| 구분 | 환경 |
|---|---|
| 가상화 | VMware Workstation |
| 운영체제 | Ubuntu 22.04 |
| 실습 계정 | user1 |
| 인증 관리 | PAM / pam_faillock |
| 정책 파일 | /etc/security/faillock.conf |
| PAM 설정 | /etc/pam.d/common-auth |

## 3. 계정 잠금 정책

| 설정 | 값 | 의미 |
|---|---|---|
| deny | 5 | 인증 실패 5회 도달 시 계정 잠금 기준 |
| unlock_time | 600 | 잠금 유지 시간 600초(10분) |
| fail_interval | 900 | 인증 실패 집계 기간 900초(15분) |

## 4. 실습 과정

1. 기존 PAM 설정 및 인증 모듈 확인
2. `faillock.conf`에 계정 잠금 정책 설정
3. `common-auth`에서 `pam_faillock.so` 연동 확인 및 수정
4. 일반 사용자 계정에서 인증 실패 테스트
5. `faillock --user user1`으로 실패 기록 5회 확인
6. 실패 기록 초기화 후 정상 인증 재검증

## 5. 결과 분석

- 계정 잠금 정책 설정값을 확인했습니다.
- `faillock`에서 유효한 인증 실패 기록 5건을 확인했습니다.
- 실패 기록이 누적된 상태에서 추가 인증 거부 현상을 관찰했습니다.
- 실패 기록 초기화 후 `user1` 계정의 `sudo whoami` 결과가 `root`로 출력되었습니다.

**검증 한계:** 추가 인증 거부가 정확히 `pam_faillock`의 계정 잠금 때문인지는 인증 로그를 통한 추가 확인이 필요합니다.

## 6. 트러블슈팅

### PAM 모듈 연동 확인

초기 `common-auth`와 `common-account` 파일에서 `pam_faillock.so` 검색 결과가 나오지 않았습니다.

이를 통해 정책 파일에 잠금 횟수를 설정하는 것과 PAM 인증 과정에 해당 모듈을 연결하는 것이 별개라는 점을 이해했습니다.

### sudo 인증 실패 횟수

`sudo` 명령의 암호 입력 재시도 횟수와 `pam_faillock`의 누적 실패 기록은 구분해야 합니다.

## 7. 보안 관점

계정 잠금 정책은 반복적인 암호 추측을 제한하는 보조 방어책입니다.

운영 환경에서는 MFA, 접근제어, 인증 로그 모니터링, 안전한 계정 복구 절차 등을 함께 고려해야 합니다.

PAM 설정을 잘못 수정하면 정상 사용자까지 인증할 수 없으므로, 변경 전 백업과 복구 수단을 확보해야 합니다.

## 8. 배운 점

- PAM 인증 모듈의 역할과 연동 구조 이해
- 인증 실패 기록 확인 및 초기화 방법 학습
- 계정 잠금 정책과 실제 인증 동작의 차이 이해
- 실습 결과와 추가 검증이 필요한 사항을 구분하는 중요성 학습

## 9. 기술 블로그

📖 [Velog — Security Engineering Blog](https://velog.io/@sunsuhak2020)

---

**Build → Secure → Verify → Improve**
