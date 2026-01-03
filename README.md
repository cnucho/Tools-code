# Tools-code – GitHub Releases 파일 배포 가이드

이 저장소는 다음 원칙으로 운영한다.

- GitHub Pages: 다운로드 허브(목록)
- GitHub Releases: 실제 파일 배포
- 파일은 필요할 때 하나씩 다운로드
- URL은 고정 유지

---

## 1. 최초 1회만 해야 하는 것 (컴퓨터마다 1회)

다른 컴퓨터에서 작업하면 다시 해야 한다.

### GitHub CLI 설치

```powershell
winget install --id GitHub.cli
```

### GitHub 로그인

```powershell
gh auth login
```

---

## 2. 업로드된 파일의 URL 확인 방법

파일명이 `normalize_gpt_urls_all.py` 인 경우:

### 최신(latest) 고정 URL

```
https://github.com/cnucho/Tools-code/releases/latest/download/normalize_gpt_urls_all.py
```

### 특정 버전 고정 URL

```
https://github.com/cnucho/Tools-code/releases/download/v0.1.0/normalize_gpt_urls_all.py
```

Pages, 티스토리에는 **latest URL만 사용**한다.

---

## 3. Release에 올라간 파일 지우는 방법

### 웹에서

- Releases → 해당 Release → Edit
- Assets에서 파일 삭제
- Update release

### PowerShell (gh)

```powershell
gh release delete-asset v0.1.0 normalize_gpt_urls_all.py --repo cnucho/Tools-code --yes
```

---

## 4. 같은 파일명으로 버전업하는 방법 (URL 유지)

파일명을 **절대 바꾸지 않는다**.

```powershell
gh release upload v0.1.0 .\normalize_gpt_urls_all.py --repo cnucho/Tools-code --clobber
```

- 기존 파일 덮어씀
- URL 그대로 유지
- 사용자는 항상 최신 파일 다운로드

---

## 5. 새 파일 올리고 URL 얻는 방법

### 새 파일 업로드

```powershell
gh release upload v0.1.0 .\analysis_runner.zip --repo cnucho/Tools-code
```

### 새 파일 URL

```
https://github.com/cnucho/Tools-code/releases/latest/download/analysis_runner.zip
```

---

## 자주 쓰는 명령

### 릴리스 목록

```powershell
gh release list --repo cnucho/Tools-code
```

### 릴리스 상세

```powershell
gh release view v0.1.0 --repo cnucho/Tools-code
```

---

## 파일명 규칙 (중요)

- 공백 ❌
- 한글 ❌
- 소문자 + underscore
- 예:
  - normalize_gpt_urls_all.py
  - analysis_runner.zip
