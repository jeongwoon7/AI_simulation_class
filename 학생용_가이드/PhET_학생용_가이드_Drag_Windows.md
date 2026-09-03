# PhET-style Electric Field Lab — Windows 학생용 실행 가이드

## 0. 이번 수업에서 사용할 것

이 실습은 **Python + Dash + Plotly + NumPy**로 만든 전기장 시뮬레이션입니다.

할 수 있는 것:
- 전하를 그래프에서 **직접 드래그**
- 전하량 `q₁`, `q₂` 변경
- 전기장 벡터 표시
- 등전위선 표시
- Probe 위치에서 `Ex`, `Ey`, `|E|`, `V` 측정

> Python은 특정 버전으로 고정하지 않습니다.  
> 프로젝트가 요구하는 호환 범위 안에서 `uv`가 환경을 관리합니다.

---

## 1. VS Code 설치

Visual Studio Code 공식 다운로드 페이지에서:

```text
Windows x64 → User Installer
```

를 선택하는 것을 권장합니다.

### User Installer를 쓰는 이유

- 관리자 권한이 없어도 설치 가능
- 개인 노트북 / 학생 PC에 적합
- 현재 Windows 사용자에게만 설치됨

다운로드한 설치 파일을 실행하고 기본 설정으로 설치합니다.

---

## 2. Python Extension 설치

VS Code 실행 후 왼쪽의 **Extensions** 아이콘을 클릭합니다.

검색창에:

```text
Python
```

을 입력하고 Microsoft의 **Python** extension을 설치합니다.

---

## 3. PowerShell 열기

VS Code 안에서 바로 여는 것이 가장 쉽습니다.

상단 메뉴:

```text
Terminal → New Terminal
```

정상적으로 PowerShell이 열리면 아래처럼 보입니다.

```powershell
PS C:\Users\학생이름\...
```

PowerShell이 아니라면 Terminal 오른쪽의 `▼` 메뉴에서:

```text
Select Default Profile → PowerShell
```

을 선택한 뒤 새 Terminal을 엽니다.

---

## 4. uv 설치

VS Code의 PowerShell에서:

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

설치 후 **VS Code를 완전히 종료했다가 다시 실행**하는 것을 권장합니다.

새 Terminal에서 확인:

```powershell
uv --version
```

버전 번호가 나오면 정상입니다.

---

## 5. 수업 프로젝트 압축 풀기

배포받은:

```text
phet_electric_field_class_drag.zip
```

을 압축 해제합니다.

예:

```text
Downloads
└─ phet_electric_field_class_drag
   ├─ app.py
   ├─ physics.py
   ├─ pyproject.toml
   └─ ...
```

---

## 6. VS Code에서 프로젝트 열기

VS Code에서:

```text
File → Open Folder
```

를 선택하고:

```text
phet_electric_field_class_drag
```

폴더를 엽니다.

---

## 7. VS Code Terminal 열기

상단 메뉴:

```text
Terminal → New Terminal
```

현재 위치가 프로젝트 폴더인지 확인합니다.

예:

```powershell
PS C:\Users\학생이름\Downloads\phet_electric_field_class_drag>
```

---

## 8. 환경 만들기

PowerShell에서:

```powershell
uv sync
```

을 실행합니다.

`uv`가 이 프로젝트에 필요한 Python 환경과 패키지를 준비합니다.

Python 확인:

```powershell
uv run python --version
```

---

## 9. 시뮬레이션 실행

```powershell
uv run python app.py
```

Terminal에 다음과 비슷한 주소가 표시됩니다.

```text
http://127.0.0.1:8050
```

`Ctrl + 클릭`하거나 브라우저 주소창에 입력합니다.

---

# 시뮬레이션 사용법

## 전하 이동

그래프의 빨간색 / 파란색 전하 원을 클릭한 뒤 **드래그**합니다.

전하를 이동하면:

```text
전하 위치 변경
      ↓
Python에서 E(x,y), V(x,y) 재계산
      ↓
전기장 / 등전위선 갱신
```

이 일어납니다.

---

## 전하량 변경

왼쪽의:

```text
q₁
q₂
```

slider를 움직입니다.

- 양수: positive charge
- 음수: negative charge
- 0: charge 없음

---

## Probe

`Probe x`, `Probe y`를 움직이면 해당 위치에서:

```text
Ex
Ey
|E|
V
```

를 확인할 수 있습니다.

---

## 표시 선택

다음을 켜거나 끌 수 있습니다.

- 전기장 벡터
- 등전위선

---

## 초기화

```text
위치 초기화
```

버튼을 누르면 전하 위치가 처음 상태로 돌아갑니다.

---

# 수업 중 생각해 볼 문제

1. 두 전하의 거리를 줄이면 중앙의 전기장은 어떻게 변할까?
2. 두 전하의 부호가 같을 때와 다를 때 무엇이 달라질까?
3. `|E| ≈ 0`이 되는 위치를 Probe로 찾아보자.
4. 전하량을 2배로 하면 같은 위치의 `|E|`와 `V`는 어떻게 변할까?
5. `physics.py`의 Coulomb 식과 화면의 변화를 연결해서 설명해 보자.

---

# 실행이 안 될 때

### `uv`를 찾을 수 없다고 나옴

VS Code를 완전히 종료한 뒤 다시 실행하고:

```powershell
uv --version
```

을 확인합니다.

그래도 안 되면 uv 설치를 다시 실행합니다.

---

### `can't open file 'app.py'`

현재 Terminal 위치가 프로젝트 폴더가 아닙니다.

VS Code에서:

```text
File → Open Folder
```

로 반드시 `phet_electric_field_class_drag` 폴더 자체를 열고 새 Terminal을 여세요.

---

### PowerShell 실행 정책 관련 메시지가 나옴

이번 수업에서는 `.venv\Scripts\Activate.ps1`을 직접 실행할 필요가 없습니다.

우리는:

```powershell
uv run python app.py
```

를 사용하므로 venv를 직접 activate하지 않아도 됩니다.

---

### 브라우저가 자동으로 열리지 않음

Terminal에 표시된:

```text
http://127.0.0.1:8050
```

을 직접 브라우저 주소창에 입력하면 됩니다.

---

## 종료

실행 중인 PowerShell에서:

```text
Ctrl + C
```

를 누르면 서버가 종료됩니다.
