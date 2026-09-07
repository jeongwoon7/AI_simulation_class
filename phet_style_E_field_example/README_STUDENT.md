# PhET-style Electric Field Lab — 수업용 Drag Edition

## 이 버전에서 달라진 점

- `physics.py`와 UI를 분리했습니다.
- **전하 원을 그래프에서 직접 드래그**할 수 있습니다.
- 전하를 움직이면 Python의 `field_and_potential()`이 다시 실행됩니다.
- **Probe**에서 `Ex`, `Ey`, `|E|`, `V`를 측정할 수 있습니다.
- 특정 Python minor version에 고정하지 않습니다.

> 드래그 기능 때문에 UI 프레임워크를 Streamlit에서 **Dash**로 바꿨습니다.
> Plotly의 editable shape 위치 변화가 Dash callback으로 전달되기 때문에,
> 위치를 바꾼 뒤 Python에서 field를 다시 계산할 수 있습니다.

## 실행

프로젝트 폴더를 VS Code에서 연 뒤 Terminal:

```text
uv sync
uv run python --version
uv run python app.py
```

브라우저에서 다음 주소를 엽니다.

```text
http://127.0.0.1:8050
```

Terminal에 표시되는 주소를 클릭해도 됩니다.

## 조작

1. 그래프의 빨강/파랑 전하 원을 클릭합니다.
2. 원을 드래그해서 위치를 바꿉니다.
3. q₁/q₂ slider로 전하량을 바꿉니다.
4. Probe x/y를 움직여 `Ex`, `Ey`, `|E|`, `V`를 관찰합니다.
5. 전기장 벡터 / 등전위선을 켜고 끌 수 있습니다.

### 참고
Plotly의 editable shape는 크기 조절 손잡이도 보여줄 수 있습니다.
이 앱은 혹시 학생이 원 크기를 바꾸더라도 **중심 위치만 받아들이고 원래 크기로 다시 그립니다.**

## 수업에서 볼 파일

- `physics.py`
  - Coulomb law
  - superposition
  - electric field
  - electric potential
  - probe measurement

- `app.py`
  - slider / checkbox
  - draggable charge
  - Plotly visualization
  - Dash callback

## 추천 실습 순서

1. q₂ = 0으로 만들고 단일 전하의 장 관찰
2. 같은 부호의 두 전하
3. 반대 부호의 두 전하(dipole)
4. 두 전하의 거리 변화
5. Probe로 `E ≈ 0` 위치 찾기
6. `physics.py`의 식과 화면의 변화를 연결해서 설명하기
