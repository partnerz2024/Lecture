# GitHub Pages 배포 및 Notion 임베딩 가이드

## GitHub Pages 배포 방법

### 1. GitHub 저장소 생성

1. [GitHub](https://github.com)에 로그인
2. 우측 상단의 **+** 버튼 클릭 → **New repository** 선택
3. 저장소 설정:
   - **Repository name**: `lecture` (또는 원하는 이름)
   - **Description**: JGSK_EDU 강의 자료실
   - **Public** 선택 (GitHub Pages 무료 사용을 위해)
   - **Initialize this repository with a README** 체크 해제
4. **Create repository** 클릭

### 2. 로컬 저장소를 GitHub에 푸시

터미널에서 다음 명령어를 실행하세요:

```bash
# GitHub 저장소 URL을 원격 저장소로 추가 (YOUR_USERNAME을 본인의 GitHub 사용자명으로 변경)
git remote add origin https://github.com/YOUR_USERNAME/lecture.git

# 기본 브랜치를 main으로 변경 (GitHub Pages는 main 브랜치를 사용)
git branch -M main

# 파일 푸시
git push -u origin main
```

### 3. GitHub Pages 활성화

1. GitHub 저장소 페이지로 이동
2. **Settings** 탭 클릭
3. 왼쪽 메뉴에서 **Pages** 클릭
4. **Source** 섹션에서:
   - **Branch**: `main` 선택
   - **Folder**: `/ (root)` 선택
5. **Save** 클릭
6. 몇 분 후 페이지가 활성화됩니다
7. 페이지 URL은 `https://YOUR_USERNAME.github.io/lecture/` 형식입니다

### 4. 비디오 파일 업로드

GitHub에는 큰 파일 업로드 제한이 있습니다 (100MB). 비디오 파일이 큰 경우:

**옵션 1: GitHub LFS 사용 (권장)**
```bash
# Git LFS 설치 후
git lfs install
git lfs track "*.mp4"
git add .gitattributes
git add videos/*.mp4
git commit -m "Add video files with LFS"
git push origin main
```

**옵션 2: 외부 스토리지 사용**
- Google Drive, Dropbox, 또는 다른 클라우드 스토리지에 비디오 업로드
- 공유 링크 생성 후 `index.html`의 경로를 외부 URL로 변경

**옵션 3: YouTube/Vimeo 사용**
- 비디오를 YouTube나 Vimeo에 업로드
- 임베드 코드를 사용하여 페이지에 통합

## Notion 임베딩 방법

### 방법 1: Notion Embed 블록 사용 (권장)

1. Notion 페이지에서 `/embed` 입력
2. **Embed** 선택
3. GitHub Pages URL 입력: `https://YOUR_USERNAME.github.io/lecture/`
4. **Embed link** 클릭
5. 페이지가 Notion에 임베드됩니다

### 방법 2: Notion Link to Page 사용

1. Notion 페이지에서 `/link` 입력
2. **Link to page** 선택
3. **Web URL** 선택
4. GitHub Pages URL 입력
5. 링크가 생성되며, 클릭하면 새 탭에서 열립니다

### 방법 3: Notion Code Block 사용

```html
<iframe 
  src="https://YOUR_USERNAME.github.io/lecture/" 
  width="100%" 
  height="800px"
  frameborder="0"
  allowfullscreen>
</iframe>
```

**참고**: Notion은 iframe을 직접 지원하지 않으므로, 이 방법은 제한적입니다.

### 방법 4: Notion Web Bookmark 사용

1. Notion 페이지에서 `/bookmark` 입력
2. GitHub Pages URL 입력
3. 미리보기 카드가 생성됩니다
4. 클릭하면 새 탭에서 열립니다

## 추천 방법

**가장 좋은 방법**: Notion Embed 블록 사용
- 페이지가 Notion 내에서 직접 표시됩니다
- 인터랙티브하게 사용 가능합니다
- 가장 깔끔한 통합입니다

## 문제 해결

### GitHub Pages가 작동하지 않는 경우

1. 저장소가 **Public**인지 확인
2. **Settings > Pages**에서 올바른 브랜치 선택 확인
3. `index.html` 파일이 루트 디렉토리에 있는지 확인
4. 몇 분 기다린 후 다시 시도 (배포에 시간이 걸릴 수 있음)

### Notion 임베드가 작동하지 않는 경우

1. GitHub Pages URL이 올바른지 확인
2. 페이지가 Public으로 설정되어 있는지 확인
3. 브라우저 콘솔에서 오류 확인
4. Notion의 Embed 블록 사용 (가장 호환성이 좋음)

## 보안 참고사항

- GitHub Pages는 Public 저장소에서만 무료로 사용 가능합니다
- 관리자 비밀번호는 클라이언트 사이드에 저장되므로 완전히 안전하지 않습니다
- 민감한 정보는 포함하지 마세요

