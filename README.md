# Excalidraw 이미지 저장소

이 저장소는 프로젝트 진행 과정에서 사용된 Excalidraw 이미지들을 관리하기 위한 공간입니다.

## 브랜치 전략

이 저장소는 브랜치 기반으로 콘텐츠를 관리합니다.

### 브랜치 구조

- **`main`**: 프로젝트에서 사용되는 모든 이미지 자산 관리
  - 각 파일의 이름은 노션(Notion)의 제목과 1대1로 매핑
  - 모든 변경사항은 **PR(Pull Request)**을 통해 처리

- **작업 브랜치**: 각자 작업을 위한 개인 브랜치
  - 브랜치명: **`type/작업내용`** 형식으로 생성 (예: `feat/proxmox-setup`)
  - 작업 완료 후 `main` 브랜치로 PR 생성
  - PR은 특정 기간에 일괄 처리

## 폴더 구조

```
study-asset/
  ├── proxmox 네트워크 설정.md  (← 노션 제목: "proxmox 네트워크 설정")
  └── ...
```

## 작업 프로세스

### 브랜치명 규칙
작업 브랜치는 **`type/작업내용`** 형식으로 생성합니다.
- `feat/proxmox-setup`: 새로운 이미지 추가
- `fix/network-diagram`: 기존 이미지 수정

### 커밋 메시지 규칙
커밋 메시지는 [Conventional Commits](https://www.conventionalcommits.org/) 형식을 따릅니다.

주요 타입:
- `feat`: 새로운 이미지 추가
- `fix`: 이미지 수정
- `docs`: 문서 수정
- `refactor`: 이미지 구조 변경

예시:
```bash
git commit -m "feat: proxmox 네트워크 설정 이미지 추가"
git commit -m "fix: 네트워크 다이어그램 오타 수정"
```

### 이미지 추가/수정 프로세스

```bash
# main 브랜치에서 작업 브랜치 생성
git checkout main
git pull origin main
git checkout -b feat/작업내용

# 작업 후 커밋
git add study-asset/파일명.md
git commit -m "feat: 이미지 설명"

# 작업 브랜치를 푸시하고 PR 생성
git push origin feat/작업내용
# → GitHub에서 main 브랜치로 PR 생성
```

### PR 처리
- PR 생성 시 제공되는 템플릿에 따라 작업 내용과 결과물 이미지를 첨부해주세요.
- PR은 특정 기간에 일괄적으로 처리합니다.
- 작업 완료 후 PR을 생성해두면, 정기적으로 리뷰 및 병합됩니다.

## 브랜치 전략의 장점

1. **단일 진실 공급원**: 모든 자산이 `main` 브랜치에서 관리됨
2. **일관된 워크플로우**: 모든 변경사항을 PR로 관리하여 리뷰 프로세스 통일
3. **히스토리 관리**: 브랜치와 커밋 메시지를 통해 변경 이력 추적 용이
