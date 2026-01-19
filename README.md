# Excalidraw 이미지 저장소

이 저장소는 책 제작 과정에서 사용된 Excalidraw 이미지들을 관리하기 위한 공간입니다.

## 브랜치 전략

이 저장소는 브랜치 기반으로 콘텐츠를 관리합니다.

### 브랜치 구조

- **`main`** (또는 `master`): 오픈소스로 공개될 예정인 책 관련 이미지들
  - 책을 만들면서 사용한 이미지들을 챕터별로 정리
  - 각 챕터는 별도의 폴더로 구분 (`chapter 1/`, `chapter 2/` 등)
  - 모든 변경사항은 **MR(Merge Request)**을 통해 처리

- **`study`**: 내부 그룹에서 관리하는 스터디 자료
  - 책을 만들기 위해 스터디에서 사용된 이미지들
  - 각 파일의 이름은 노션(Notion)의 제목과 1대1로 매핑
  - 내부 그룹에서 관리하며, 오픈소스 공개 대상 아님
  - 변경사항은 **MR(Merge Request)**을 통해 `study` 브랜치로 병합

- **작업 브랜치**: 각자 작업을 위한 개인 브랜치
  - 브랜치명: **본인 이름**으로 생성
  - 작업 완료 후 해당 목적지 브랜치(`main` 또는 `study`)로 MR 생성
  - MR은 특정 기간에 일괄 처리

## 폴더 구조

### `main` 브랜치
```
book/
  ├── chapter 1/
  │   └── 오픈스택이란?.md
  └── chapter 2/
      └── ...
```

### `study` 브랜치
```
docs/
  ├── proxmox 네트워크 설정.md  (← 노션 제목: "proxmox 네트워크 설정")
  └── ...
```

## 작업 프로세스

### 브랜치명 규칙
- 작업 브랜치는 **본인 이름**으로 생성합니다
- 예: `홍길동`, `김철수` 등

### 커밋 메시지 규칙
커밋 메시지는 [Conventional Commits](https://www.conventionalcommits.org/) 형식을 따릅니다.

주요 타입:
- `feat`: 새로운 이미지 추가
- `fix`: 이미지 수정
- `docs`: 문서 수정
- `refactor`: 이미지 구조 변경

예시:
```bash
git commit -m "feat: chapter 1 오픈스택 소개 이미지 추가"
git commit -m "fix: proxmox 네트워크 설정 이미지 수정"
```

### 1. 책 이미지 추가 (오픈소스 예정)

```bash
# main 브랜치에서 작업 브랜치 생성
git checkout main
git pull origin main
git checkout -b 본인이름

# 작업 후 커밋
git add book/chapter\ 1/오픈스택이란?.md
git commit -m "feat: chapter 1 오픈스택 소개 이미지 추가"

# 작업 브랜치를 푸시하고 MR 생성
git push origin 본인이름
# → GitLab/GitHub에서 main 브랜치로 MR 생성
```

### 2. 스터디 이미지 추가 (내부 관리)

```bash
# study 브랜치에서 작업 브랜치 생성
git checkout study
git pull origin study
git checkout -b 본인이름

# 작업 후 커밋
git add docs/proxmox\ 네트워크\ 설정.md
git commit -m "feat: proxmox 네트워크 설정 이미지 추가"

# 작업 브랜치를 푸시하고 MR 생성
git push origin 본인이름
# → GitLab/GitHub에서 study 브랜치로 MR 생성
```

### MR 처리
- MR은 특정 기간에 일괄적으로 처리합니다
- 작업 완료 후 MR을 생성해두면, 정기적으로 리뷰 및 병합됩니다

## 브랜치 전략의 장점

1. **명확한 구분**: 오픈소스 공개 예정(`main`)과 내부 자료(`study`)를 브랜치로 분리
2. **권한 관리**: 브랜치별로 보호 규칙 설정 가능
3. **오픈소스 공개 용이**: 공개 시 `main` 브랜치만 공개하면 됨
4. **일관된 워크플로우**: 모든 변경사항을 MR로 관리하여 리뷰 프로세스 통일

