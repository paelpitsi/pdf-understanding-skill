# PDF Understanding Skill for OpenCode

Преобразует PDF в структурированный markdown с извлечением текста,
описанием диаграмм и генерацией mermaid-схем.

## Установка

1. Скопировать `.opencode/` в корень папки с PDF
2. Добавить `opencode.json` (или смержить с существующим)
3. Установить poppler-utils:
   - Windows: `winget install --id=oschwartz10612.Poppler -e`
   - macOS: `brew install poppler`
   - Linux: `apt install poppler-utils`

## Использование

В opencode:
```
Use pdf-understanding skill on lecture.pdf
```

Результат: `output/<имя>.md`

## Зависимости

- poppler-utils (pdftoppm)
- OpenCode Zen API ключ (бесплатно для MiMo V2.5 Free)
