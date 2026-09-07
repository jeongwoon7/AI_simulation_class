# PhET-style Electric Field Lab — macOS 학생용 실행 가이드

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

1. 브라우저에서 **Visual Studio Code** 공식 사이트로 이동
2. **macOS** 버전 다운로드
3. 다운로드한 `.dmg` 파일 실행
4. **Visual Studio Code**를 `Applications` 폴더로 이동
5. VS Code 실행

---

## 2. Python Extension 설치

VS Code 왼쪽의 **Extensions** 아이콘을 클릭합니다.

검색창에:

```text
Python
```

입력 후, Microsoft의 **Python** extension을 설치합니다.

---

## 3. uv 설치

macOS의 **Terminal** 앱을 열고 아래 명령을 실행합니다.

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

설치 후 Terminal을 닫았다가 다시 열고 확인합니다.

```bash
uv --version
```

버전 번호가 나오면 정상입니다.

---

## 4. 수업 프로젝트 압축 풀기

배포받은:

```text
phet_electric_field_class_drag.zip
```

을 압축 해제합니다.

예:

```text
Downloads/
└── phet_electric_field_class_drag/
    ├── app.py
    ├── physics.py
    ├── pyproject.toml
    └── ...
```

---

## 5. VS Code에서 프로젝트 열기

VS Code에서:

```text
File → Open Folder
```

를 선택하고,

```text
phet_electric_field_class_drag
```

폴더를 엽니다.

---

## 6. VS Code Terminal 열기

VS Code 상단 메뉴:

```text
Terminal → New Terminal
```

아래쪽에 Terminal이 열립니다.

현재 위치가 프로젝트 폴더인지 확인합니다.

예:

```text
.../phet_electric_field_class_drag %
```

---

## 7. 환경 만들기

VS Code Terminal에서:

```bash
uv sync
```

을 실행합니다.

`uv`가 이 프로젝트에 필요한 Python 환경과 패키지를 준비합니다.

설치된 Python 확인:

```bash
uv run python --version
```

---

## 8. 시뮬레이션 실행

```bash
uv run python app.py
```

Terminal에 다음과 비슷한 주소가 표시됩니다.

```text
http://127.0.0.1:8050
```

주소를 `Command + 클릭`하거나 브라우저에 입력합니다.

---

# 시뮬레이션 사용법

## 전하 이동

그래프의 빨간색 / 파란색 전하 원을 클릭하고 **드래그**합니다.

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

### `uv: command not found`

Terminal을 완전히 닫았다가 다시 열고:

```bash
uv --version
```

을 다시 확인합니다.

그래도 안 되면 uv 설치를 다시 실행합니다.

---

### `No such file: app.py`

현재 Terminal 위치가 프로젝트 폴더가 아닙니다.

VS Code에서 반드시:

```text
File → Open Folder
```

로 `phet_electric_field_class_drag` 폴더를 연 뒤 새 Terminal을 여세요.

---

### 브라우저가 자동으로 열리지 않음

Terminal에 표시된:

```text
http://127.0.0.1:8050
```

을 직접 브라우저 주소창에 입력하면 됩니다.

---

## 종료

실행 중인 Terminal에서:

```text
Control + C
```

를 누르면 서버가 종료됩니다.
