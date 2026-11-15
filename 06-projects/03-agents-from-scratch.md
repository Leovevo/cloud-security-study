---
title: "Pguso/agents-from-scratch"
date: 2026-09-29
updated: 2026-11-11
category: "프로젝트"
tags: ["dailyCoding"]
original: https://velog.io/@xjoker7272/Pgusoagents-from-scratch
---

> **AI 에이전트 밑바닥부터 만들기 — Day 1**
> [pguso/agents-from-scratch](https://github.com/pguso/agents-from-scratch)를 fork해서, 프레임워크 없이 로컬 LLM으로 에이전트를 직접 만들어 보는 학습 기록입니다.

## TL;DR

- Windows에서 `pip install llama-cpp-python`이 실패했다.
- 처음엔 **"Python 3.14용 wheel이 없어서"** 라고 추측하고 3.12로 다운그레이드했다. **틀린 추측이었다.**
- 진짜 원인은 **Windows 경로 길이 제한(MAX_PATH = 260자)** 이었다.
- `LongPathsEnabled = 1`로 설정하자 소스 빌드까지 성공했다.
- 교훈: **마지막 에러가 아니라, 맨 처음 발생한 에러를 봐야 한다.**

---

## 1. 문제 상황

환경은 이렇다.

- Windows 11, Python 3.14
- 모델: `llama-3-8b-instruct.gguf` (Q4_K_M)
- 의존성: `llama-cpp-python` 하나

`pip install -r requirements.txt`를 실행한 뒤 import를 해 보니 이런 에러가 났다.

```
ModuleNotFoundError: No module named 'llama_cpp'
```

## 2. 첫 번째 가설: "Python 3.14가 너무 최신이라서?"

`llama-cpp-python`은 C++로 작성된 llama.cpp를 감싼 **네이티브 확장 패키지**다. 3.14는 나온 지 얼마 안 된 버전이니, 미리 빌드된 wheel이 아직 없을 거라고 추측했다.

그래서 Python 3.12를 설치하고 venv를 다시 만들었다.

```powershell
deactivate
Remove-Item -Recurse -Force venv
py -3.12 -m venv venv
.\venv\Scripts\Activate.ps1
python --version   # Python 3.12.10
```

> 💡 활성화된 venv를 그대로 지우려고 하면, Windows가 사용 중인 파일을 잠가 두기 때문에 삭제에 실패할 수 있다. 먼저 `deactivate`부터 하자.

그리고 다시 설치를 시도했더니...

## 3. 3.12에서도 실패했다

```
Collecting llama-cpp-python (from -r requirements.txt (line 1))
  Using cached llama_cpp_python-0.3.35.tar.gz (74.9 MB)
ERROR: Could not install packages due to an OSError: [Errno 2] No such file or directory:
'C:\\Users\\<사용자>\\AppData\\Local\\Temp\\pip-install-r8zmuqbf\\llama-cpp-python_1e14396b...\\vendor\\llama.cpp\\tools\\ui\\src\\lib\\components\\app\\chat\\ChatAttachments\\ChatAttachmentsList\\ChatAttachmentsListItem\\ChatAttachmentsListItemMcpResource.svelte'
```

이 로그에 단서가 세 개 있다.

1. **`Using cached ....tar.gz`**: wheel이 아니라 **소스 배포판(sdist)** 을 받았다. 게다가 `cached`, 즉 **3.14 때 받아 둔 바로 그 파일**을 다시 썼다.
2. **실패한 시점**: 컴파일 단계가 아니라, **압축을 푸는 단계**에서 실패했다.
3. **에러 메시지 속 경로**: 눈으로 봐도 비정상적으로 길다.

## 4. 진짜 원인: MAX_PATH (260자)

Windows에는 **파일 경로 하나가 260자를 넘을 수 없다**는 오래된 제한(`MAX_PATH`)이 있다.

```
C:\Users\<사용자>\AppData\Local\Temp\pip-install-xxxx\llama-cpp-python_<32자 해시>\   ← pip 임시 폴더 (원래부터 김)
  + vendor\llama.cpp\tools\ui\src\lib\components\app\chat\...\ChatAttachmentsListItemMcpResource.svelte   ← llama.cpp 웹 UI의 깊은 폴더
  = 260자 초과 → "No such file or directory"
```

레지스트리를 확인해 보니 긴 경로 지원이 꺼져 있었다(`LongPathsEnabled = 0`).

### 가설이 틀렸다는 증거 두 가지

| 증거 | 의미 |
|---|---|
| 3.12에서도 **같은 캐시 sdist**로 **같은 방식으로** 실패했다 | Python 버전을 바꿔도 결과가 같으니, 원인은 버전이 아니다 |
| 빌드된 wheel 이름이 `...-py3-none-win_amd64.whl` | `cp314`처럼 특정 버전용이 아니라 **Python 3 공용**이다. "3.14용 wheel이 없다"는 전제 자체가 성립하지 않는다 |

(3.14 때의 pip 로그는 따로 확인하지 못했기 때문에, 그때도 같은 원인이었다는 건 **정황상 추정**이다.)

## 5. 해결: 긴 경로 지원 켜기

**관리자 권한**으로 터미널을 연 뒤 아래 중 하나를 실행한다.

**PowerShell**
```powershell
New-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" -Name LongPathsEnabled -Value 1 -PropertyType DWORD -Force
```

**cmd (명령 프롬프트)**
```
reg add "HKLM\SYSTEM\CurrentControlSet\Control\FileSystem" /v LongPathsEnabled /t REG_DWORD /d 1 /f
```

**적용 확인**
```
reg query "HKLM\SYSTEM\CurrentControlSet\Control\FileSystem" /v LongPathsEnabled
# → 0x1 이면 성공
```

> ⚠️ 나는 관리자 권한으로 **cmd**를 열어 놓고 PowerShell 명령어를 붙여 넣는 바람에 `'New-ItemProperty'은(는) 내부 또는 외부 명령...이 아닙니다`라는 에러를 봤다. 프롬프트 앞에 `PS`가 없으면 cmd다.

> 💡 레지스트리를 건드리기 싫다면, 현재 셸에서만 임시 폴더를 짧은 경로로 바꾸는 우회 방법도 있다.
> `$env:TMP="C:\t"; $env:TEMP="C:\t"`

VS Code 터미널을 새로 열고 다시 설치했다.

```
Created wheel for llama-cpp-python: filename=llama_cpp_python-0.3.35-py3-none-win_amd64.whl
Successfully built llama-cpp-python
Successfully installed ... llama-cpp-python-0.3.35 ...
```

```powershell
python -c "import llama_cpp; print(llama_cpp.__version__)"
# 0.3.35
```

## 6. 소스 빌드가 성공한 과정

Python이 C++를 직접 컴파일한 게 아니다. **pip는 현장 감독**이고, 실제 컴파일은 **C++ 컴파일러**가 한다.

| 순서 | 누가 | 무엇을 |
|---|---|---|
| 1 | pip | sdist 압축 해제 (이번엔 긴 경로가 허용돼서 통과) |
| 2 | pip | `pyproject.toml`을 읽고 빌드 도구(CMake 등) 준비 |
| 3 | CMake | PC에 설치된 컴파일러 탐색 → Visual Studio Build Tools (MSVC) |
| 4 | MSVC | llama.cpp C++ 코드를 컴파일해서 `llama.dll` 생성 |
| 5 | pip | DLL과 Python 코드를 wheel로 포장한 뒤 venv에 설치 |
| 6 | Python | `import llama_cpp` 할 때 `ctypes`로 DLL을 불러옴 |

> Build Tools(C++ 컴파일러)가 설치돼 있지 않았다면 3단계에서 `No CMAKE_CXX_COMPILER could be found` 같은 에러가 났을 것이다.

## 7. 보안 관점에서 다시 보기

`pip install`로 sdist를 설치한다는 건, **인터넷에서 받은 빌드 스크립트를 내 계정 권한으로 실행한다**는 뜻이다. 패키지가 변조돼 있었다면, 설치하는 순간 SSH 키나 클라우드 자격증명에 접근할 수 있다. 이게 **공급망 공격**이 들어오는 통로다.

현업에서 쓰는 대응 방법은 이렇다.

- 버전 고정 + 해시 검증 (`--require-hashes`)
- wheel만 허용 (`--only-binary :all:`): 설치할 때 빌드 코드가 실행되지 않는다
- 컨테이너나 샌드박스 안에서 빌드
- 내부 미러, 허용 목록 운영

그리고 **venv는 보안 경계가 아니다.** venv는 패키지 목록만 분리할 뿐, 파일이나 네트워크 접근은 전혀 막지 않는다. 앞으로 만들 에이전트가 도구를 실행하게 되면 같은 질문을 마주하게 된다. **"누구의 권한으로, 어디서 실행되는가?"**

## 8. 용어 정리

| 용어 | 설명 |
|---|---|
| **venv** | virtual environment. 프로젝트별 패키지 공간. 같은 집 안에서 **내 책장만 따로 쓰는 것**이다. 책(패키지)은 섞이지 않지만, 집 안의 모든 방(파일, 네트워크)에는 그대로 드나들 수 있다. 샌드박스가 아니다 |
| **sdist** | source distribution. 컴파일하기 전의 원재료 묶음(`.tar.gz`). **밀키트**처럼 내 PC에서 직접 조리(빌드)해야 한다 |
| **wheel** | 미리 빌드된 설치 파일(`.whl`). **완제품 도시락**처럼 받아서 바로 설치하면 된다 |
| **MAX_PATH** | Windows에서 파일 경로 하나에 쓸 수 있는 최대 길이(260자) |
| **MSVC / Build Tools** | MSVC는 마이크로소프트의 C/C++ 컴파일러, Build Tools는 IDE 없이 MSVC만 설치하는 패키지 |
| **컴파일러** | 소스 코드를 CPU가 실행할 수 있는 기계어로 미리 번역하는 프로그램 |

### wheel 파일 이름 읽는 법

`llama_cpp_python-0.3.35-py3-none-win_amd64.whl`

| 부분 | 뜻 |
|---|---|
| `0.3.35` | 패키지 버전 |
| `py3` | Python 3이면 어떤 버전이든 사용 가능 |
| `none` | 특정 Python ABI에 묶이지 않음 |
| `win_amd64` | 64비트 Windows 전용 |

## 9. 오늘의 교훈

1. **`ModuleNotFoundError`는 결과일 뿐이다.** 원인은 그 앞의 `pip install` 로그에 있다. 맨 처음 발생한 에러부터 보자.
2. **버전을 바꿔서 해결됐더라도, 왜 해결됐는지 로그로 확인하자.** 이번에는 버전을 바꿔도 해결되지 않았기 때문에 가설이 틀렸다는 걸 알 수 있었다.
3. **Windows에서 네이티브 패키지 설치가 실패하면** 경로 길이 제한(MAX_PATH)과 C++ 빌드 도구 설치 여부를 먼저 의심하자.

## 다음 글

Lesson 01: 로컬 LLM과 기본 채팅. `setup_check.py`는 모델 **파일이 있는지만** 확인했기 때문에, 실제로 모델이 로드되고 응답하는지는 다음 글에서 처음 검증한다.
