# Windows 실행 요약

VS Code와 uv가 설치되어 있다는 가정입니다.

```powershell
uv sync
uv run python --version
uv run python app.py
```

Terminal에 나오는 `http://127.0.0.1:8050`을 브라우저에서 엽니다.

VS Code Python interpreter가 필요하면:
`Ctrl + Shift + P` → `Python: Select Interpreter` → 프로젝트의 `.venv\Scripts\python.exe`
