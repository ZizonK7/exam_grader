# exam_grader

Firebase 기반 웹 시험 채점기입니다. 관리자가 시험(30문항)과 정답을 등록하면, 사용자가 답안을 입력해 즉시 채점하고 결과를 Firestore에 저장할 수 있습니다.

## 주요 기능

- 시험 선택 후 30문항 답안 채점
- 문항별 배점 반영 자동 점수 계산
- 오답/미입력 문항 상세 표시
- 내 시험 결과 조회 및 오답 상세 확인
- 번호대별/문항별 정답률 통계
- 관리자 로그인 후 시험 등록/목록 조회/삭제
- 관리자용 전체 채점 기록 조회, 점수 수정, 기록 삭제
- OMR 이미지 업로드 후 답안 자동 입력 지원 (`index.html`)

## 프로젝트 구조

- `/home/runner/work/exam_grader/exam_grader/index.html`: 메인 버전 (OMR 자동 입력 포함)
- `/home/runner/work/exam_grader/exam_grader/backup.html`: 백업 버전 (OMR 기능 없음)

## 실행 방법

별도 빌드 과정 없이 정적 HTML로 동작합니다.

1. 저장소를 클론합니다.
2. `/home/runner/work/exam_grader/exam_grader/index.html` 파일을 브라우저에서 엽니다.

> Firebase 설정이 유효하지 않으면 채점 결과 온라인 저장/조회 기능은 비활성화됩니다.

## Firebase 설정

`index.html`(또는 `backup.html`)의 아래 값을 본인 프로젝트 값으로 교체해야 합니다.

- `firebaseConfig`
- `ADMIN_UID`

필요한 Firebase 서비스:

- Authentication (이메일/비밀번호)
- Cloud Firestore

## Firestore 데이터

앱은 기본적으로 다음 컬렉션을 사용합니다.

- `exams`: 시험 정보(제목, 정답 배열, 문항 수, 만점, 생성일)
- `examRecords`: 채점 결과(점수, 정오답, 제출 답안, 생성일 등)

## 주의 사항

- 관리자 기능은 로그인 사용자 UID가 `ADMIN_UID`와 일치할 때만 활성화됩니다.
- Firestore 보안 규칙을 반드시 프로젝트 정책에 맞게 설정하세요.
- 현재 저장소에는 테스트/빌드 스크립트가 포함되어 있지 않습니다.
