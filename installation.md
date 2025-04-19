# Установка LaTeX и настройка Visual Studio Code через Chocolatey

## 1. Установка Chocolatey

1. **Откройте PowerShell от имени администратора:**
   - Нажмите Win → найдите `PowerShell` → ПКМ → *Запустить от имени администратора*.

2. **Вставьте и выполните эту команду:**
   ```powershell
   @"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
   ```

3. **Проверьте установку:**
   ```powershell
   choco --version
   ```

---

## 2. Установка LaTeX (MiKTeX)

1. **Установите MiKTeX через Chocolatey:**
   ```powershell
   choco install miktex -y
   ```

2. **После установки запустите MiKTeX Console (если нужно), чтобы настроить автоустановку пакетов.**

---

## 3. Установка Visual Studio Code

1. **Установите VS Code через Chocolatey:**
   ```powershell
   choco install vscode -y
   ```

2. **Запустите Visual Studio Code из меню "Пуск".**

---

## 4. Настройка VS Code для работы с LaTeX

1. **Установите расширение LaTeX Workshop:**
   - Откройте VS Code.
   - Нажмите `Ctrl+P`, введите:
     ```
     ext install James-Yu.latex-workshop
     ```
## 5. Проверка

1. **Создайте файл `hello.tex`:**
   ```latex
   \documentclass{article}
   \begin{document}
   Hello, world!
   \end{document}
   ```

2. **Сохраните файл и нажмите `Ctrl+Alt+B`.**
3. **В правой части появится окно предпросмотра PDF.**

---

## Полезные команды

---

## 🔗 Ссылки

- Chocolatey: https://chocolatey.org/
- MiKTeX: https://miktex.org/
- Visual Studio Code: https://code.visualstudio.com/
- Расширение LaTeX Workshop: https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop
