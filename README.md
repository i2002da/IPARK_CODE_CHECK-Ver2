[README.md](https://github.com/user-attachments/files/25619680/README.md)
# 📋 내역 코드 체크 시스템

> 원내역 ↔ 자재리스트·일위대가리스트 코드 검토 및 표준내역 항목 비교 웹 애플리케이션

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-배포중-success?logo=github)](https://pages.github.com)
[![HTML](https://img.shields.io/badge/HTML-Single%20File-orange?logo=html5)](.)
[![License](https://img.shields.io/badge/License-Private-red)](.)

---

## 📌 목차

- [개요](#-개요)
- [주요 기능](#-주요-기능)
- [사용 방법](#-사용-방법)
- [로그인 및 계정 관리](#-로그인-및-계정-관리)
- [GitHub Pages 배포](#-github-pages-배포)
- [파일 구조](#-파일-구조)
- [기술 스택](#-기술-스택)

---

## 🔍 개요

건설 내역 업무에서 발생하는 **코드 불일치·누락 문제를 자동으로 검토**하는 단일 HTML 파일 웹 애플리케이션입니다.  
별도 서버 설치 없이 브라우저만으로 실행되며, GitHub Pages를 통해 팀 전체가 웹에서 접근할 수 있습니다.

---

## ✨ 주요 기능

### 1. 코드 검토
| 상태 | 설명 |
|------|------|
| ✅ 일치 | 원내역 코드가 DB(자재·일위대가)에 존재하며 품명 일치 |
| ⚠️ 코드 상이 | 코드는 있으나 품명·규격·단위가 다름 |
| ❌ DB 없음 | 원내역 코드가 자재리스트·일위대가리스트에 없음 |
| ➖ 미확인 | 코드 없이 품명만 있는 항목 |

### 2. 표준내역 비교
| 상태 | 설명 |
|------|------|
| ⚡ 원내역만 존재 | 원내역에는 있으나 표준내역에 없는 항목 |
| 📎 표준내역만 존재 | 표준내역에는 있으나 원내역에 없는 항목 |
| ✅ 양쪽 모두 존재 | 두 내역 모두에 코드 존재 |

### 3. 결과 저장
- 검토 결과를 **Excel(.xlsx)** 파일로 내보내기

### 4. 사용자 인증
- 로그인 기반 접근 제어
- 마스터 / 일반 사용자 권한 분리
- 비밀번호 변경 기능

---

## 🚀 사용 방법

### 파일 업로드

```
① 원내역 파일 (.xlsx / .xlsm / .xls)          ← 필수
② 자재리스트 파일 (.xlsx / .xlsm / .xls)       ← 코드 검토 시 필요
③ 일위대가리스트 파일 (.xlsx / .xlsm / .xls)   ← 코드 검토 시 필요
④ 표준내역 파일 (.xlsx / .xlsm / .xls)         ← 표준내역 비교 시 필요
```

> 파일은 드래그 앤 드롭 또는 클릭하여 업로드할 수 있습니다.

### 엑셀 파일 요구사항

각 파일의 시트에는 아래 컬럼 헤더가 포함되어 있어야 합니다.

| 컬럼명 | 설명 | 필수 여부 |
|--------|------|-----------|
| `코드` | 자재·공종 코드 | 필수 |
| `품명` | 항목 이름 | 필수 |
| `규격` | 규격 정보 | 선택 |
| `단위` | 단위 정보 | 선택 |

### 검토 실행

1. **코드 검토 실행** — 원내역 + 자재리스트/일위대가리스트 업로드 후 클릭
2. **표준내역 비교** — 원내역 + 표준내역 업로드 후 클릭
3. **결과 저장** — 검토 완료 후 Excel 파일로 내보내기
4. **초기화** — 모든 업로드 파일 및 결과 초기화

---

## 🔐 로그인 및 계정 관리

### 기본 계정

| 아이디 | 비밀번호 | 권한 |
|--------|----------|------|
| `master` | `master1234` | 마스터 (관리자) |
| `user1` | `user1234` | 일반 사용자 |

> ⚠️ **최초 배포 후 반드시 비밀번호를 변경하세요.**

### 권한별 기능

| 기능 | 일반 사용자 | 마스터 |
|------|:-----------:|:------:|
| 코드 검토 / 표준내역 비교 | ✅ | ✅ |
| 결과 Excel 저장 | ✅ | ✅ |
| 내 비밀번호 변경 | ✅ | ✅ |
| 사용자 추가 / 삭제 | ❌ | ✅ |
| 사용자 활성화 / 비활성화 | ❌ | ✅ |
| 타 사용자 비밀번호 변경 | ❌ | ✅ |

### 비밀번호 변경

1. 로그인 후 헤더의 **🔐 비밀번호 변경** 클릭
2. 현재 비밀번호 입력 후 새 비밀번호 설정
3. 마스터는 **👥 사용자 비밀번호 변경** 탭에서 타 계정 비밀번호 직접 변경 가능

### 데이터 저장 방식

사용자 정보(계정 목록, 비밀번호 등)는 브라우저의 **`localStorage`** 에 저장됩니다.
- GitHub Pages 도메인에 종속되어 영구 저장됩니다.
- 같은 URL로 접속하는 모든 사용자가 동일한 계정 DB를 공유합니다.
- 브라우저 캐시/데이터를 초기화하면 계정 정보가 기본값으로 리셋됩니다.

---

## 🌐 GitHub Pages 배포

### 최초 배포

```bash
# 1. 저장소 클론 또는 신규 생성
git init
git remote add origin https://github.com/{username}/{repository}.git

# 2. 파일 추가 및 커밋
cp CodeCheck_ipark_v5.html index.html
git add index.html README.md
git commit -m "feat: 내역 코드 체크 시스템 초기 배포"
git push -u origin main
```

### GitHub Pages 설정

```
Repository → Settings → Pages
  Source : Deploy from a branch
  Branch : main / (root)
  → Save
```

접속 주소: `https://{username}.github.io/{repository}/`

### 업데이트 배포

```bash
git add index.html
git commit -m "fix: 버그 수정 / feat: 기능 추가"
git push
```

---

## 📁 파일 구조

```
repository/
│
├── index.html        # 메인 애플리케이션 (단일 파일)
└── README.md         # 프로젝트 설명서 (이 파일)
```

> 모든 기능(HTML + CSS + JavaScript)이 `index.html` 단일 파일에 포함되어 있습니다.

---

## 🛠 기술 스택

| 기술 | 용도 |
|------|------|
| HTML5 / CSS3 | UI 구조 및 스타일 |
| Vanilla JavaScript (ES6+) | 애플리케이션 로직 |
| [SheetJS (xlsx)](https://sheetjs.com) `v0.18.5` | Excel 파일 읽기·쓰기 |
| [Noto Sans KR](https://fonts.google.com/noto/specimen/Noto+Sans+KR) | 한글 폰트 |
| [JetBrains Mono](https://www.jetbrains.com/legalnotices/font_license/) | 코드·숫자 폰트 |
| localStorage | 사용자 계정 데이터 영속 저장 |
| GitHub Pages | 웹 호스팅 |

---

## 📝 버전 히스토리

| 버전 | 내용 |
|------|------|
| v5 | GitHub Pages 대응 — localStorage 영속 저장 |
| v4 | HTML 파일 자체 저장 방식 (로컬 전용) |
| v3 | 사용자 삭제 버그 수정 (esc 함수 순서, 이벤트 위임) |
| v2 | 비밀번호 변경 기능 추가 |
| v1 | 로그인 / 사용자 관리 기능 추가 |
| v0 | 코드 검토 / 표준내역 비교 초기 버전 |

---

<div align="center">
  <sub>아이파크 건설 · 내역관리팀</sub>
</div>
