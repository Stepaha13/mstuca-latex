# LaTeX

Ниже приведён пример возможностей языка LaTeX для подготовки отчётов по лабораторным работам.
[Методичка](http://www.stolyarov.info/books/pdf/latex3days.pdf).

---

## 1. Структура документа

```latex
\documentclass[12pt,a4paper]{article}      % Выбор класса документа
\usepackage[T2A]{fontenc}                  % Поддержка кириллицы
\usepackage[utf8]{inputenc}                % Кодировка UTF-8
\usepackage[russian]{babel}                % Локализация: переносы, названия
% Подключение основных пакетов
\usepackage{amsmath,amssymb,mathtools}      % Расширенные возможности математики
\usepackage{graphicx}                      % Работа с графикой
\usepackage{geometry}                      % Настройка полей страницы
\geometry{left=3cm,right=2cm,top=2.5cm,bottom=2.5cm}
\usepackage{hyperref}                      % Гиперссылки в документе
\usepackage{caption, subcaption}           % Подписи и субфигуры
\usepackage{booktabs}                      % Качественные таблицы
\usepackage{listings}                      % Набор кода
\usepackage{xcolor}                        % Цветовые настройки
\usepackage{tikz}                          % Векторная графика
\usepackage{biblatex}                      % Библиография
\addbibresource{references.bib}            % Файл библиографии
```  

---

## 2. Заголовок, титульная страница и оглавление

### 2.1. Простой заголовок и оглавление

```latex
\title{Отчёт по лабораторной работе: Исследование XYZ}
\author{Иванов И.\,И. \\
Группа КТ-101}
\date{\today}

\begin{document}
  \maketitle        % Генерирует заголовок
  \tableofcontents % Оглавление
  \newpage         % Новая страница после оглавления
```

### 2.2. Расширенная титульная страница

```latex
% Пакет для гибкой настройки титульной страницы
\usepackage{titling}

% Настройка форматирования
\pretitle{\begin{center}\Large\bfseries}
\posttitle{\par\end{center}\vskip 0.5em}
\preauthor{\begin{center}\normalsize}
\postauthor{\par\end{center}}
\predate{\begin{center}\small}
\postdate{\par\end{center}}
```

**Возможности:**
- **Логотип:**
  ```latex
  \usepackage{graphicx}
  \pretitle{\begin{center}
    \includegraphics[width=0.2\textwidth]{logo.png}\\[1em]
    \LARGE\bfseries
  }\posttitle{\par\end{center}\vskip 0.5em}
  ```
- **Подзаголовок и благодарности:**
  ```latex
  \subtitle{Подзаголовок работы}
  \thanks{Автор благодарит проф. Петрова за консультации}
  ```
- **Несколько авторов:**
  ```latex
  \author{
    Иванов И.\,И.  \and
    Петров П.\,П. \and
    Сидорова С.\,А.
  }
  ```

### 2.3. Настройка оглавления

```latex
\usepackage{tocloft}               % Пакет для управления оглавлением
\setlength{\cftbeforesecskip}{2pt} % Отступ перед секциями
\setlength{\cftsecindent}{0pt}     % Отступ секций
\renewcommand{\contentsname}{Содержание} % Переименование
```

---

## 3. Текст, шрифты и списки

### 3.1. Стиль текста

- **Размеры шрифта:** `\tiny`, `\scriptsize`, `\footnotesize`, `\small`, `\normalsize`, `\large`, `\Large`, `\LARGE`, `\huge`, `\Huge`.
- **Семейства шрифтов:** `\textrm{Римский}`, `\textsf{Ариал}`, `\texttt{Моно}`.
- **Выравнивание:**
  ```latex
  \begin{flushleft}Левый край\end{flushleft}
  \begin{center}По центру\end{center}
  \begin{flushright}Правый край\end{flushright}
  ```

### 3.2. Спецсимволы и типографика

- **Кавычки (рус.):** `<<текст>>` или `„текст“`.
- **Тире и дефис:** `--` (–), `---` (—), `-` (-).
- **Эллипсис:** `\ldots` → …
- **Апостроф/ударение:** `\textquotesingle`, ``\`{}``.

### 3.3. Списки

#### 3.3.1. Маркированные и нумерованные

```latex
\usepackage{enumitem}  % Тонкая настройка списков
\begin{itemize}[label=--, topsep=0pt]
  \item Пункт 1
  \item Пункт 2
    \begin{enumerate}[label=\arabic*), leftmargin=*]
      \item Подпункт 1
      \item Подпункт 2
    \end{enumerate}
\end{itemize}
```

#### 3.3.2. Описание (description)

```latex
\begin{description}[style=nextline]
  \item[Переменная~\(x\)] Описание переменной \(x\).
  \item[Константа~\(c\)] Описание константы \(c\).
\end{description}
```

### 3.4. Выноски и примечания

```latex
Текст с ссылкой на примечание\footnote{Содержание выноски.}
```

*Выноски автоматически нумеруются.*

---

## 4. Математика и формулы

### 4.1. Встроенные формулы

```latex
Задача: вычислить $f(x) = e^{-x^2} \cdot \sin(x)$ на интервале $[0,1]$.
```

### 4.2. Отдельные (display) формулы

```latex
\[ I = \int_0^1 e^{-x^2} \sin(x) \, dx \]
```

### 4.3. Многострочные формулы (align)

```latex
\begin{align}
  y &= x^2 + 2x + 1 \\
  &= (x+1)^2.
\end{align}
```  
*`align*` — без нумерации строк.*

### 4.4. Системы уравнений

```latex
\begin{cases}
  \dot x = \sigma (y - x),\\
  \dot y = x (\rho - z) - y,\\
  \dot z = x y - \beta z.
\end{cases}
```  
*Окружение `cases`/`cases*` из пакета `mathtools`.*

### 4.5. Матрицы и определители

```latex
\begin{bmatrix}
  a & b \\
  c & d
\end{bmatrix},
\quad
\begin{vmatrix}
  1 & 2 & 3 \\
  0 & -1 & 4 \\
  5 & 0 & 2
\end{vmatrix}.
```  
*Окружения: `matrix`, `pmatrix`, `bmatrix`, `vmatrix`, `Vmatrix`.*

### 4.6. Теоремы, определения и доказательства

```latex
\usepackage{amsthm}
\newtheorem{theorem}{Теорема}[section]
\newtheorem{definition}[theorem]{Определение}

\begin{definition}
  Группа — это множество с операцией, удовлетворяющей …
\end{definition}

\begin{theorem}[Пример теоремы]
  Содержательное утверждение теоремы.
\end{theorem}

\begin{proof}
  Доказательство проводится следующим образом:
  …
\end{proof}
```

### 4.7. Дополнительно

- **Нумерация по разделам:** `\numberwithin{equation}{section}` (из `amsmath`).
- **Операторы и функции:** `\DeclareMathOperator{\Дирихлет}{Dir}`.
- **Формулы химии:** `\usepackage{mhchem}`: `\ce{H2O}`.
- **Диаграммы коммутативности:** `\usepackage{tikz-cd}`

```latex
\begin{tikzcd}
  A \arrow{r}{f} \arrow{d}[swap]{g} & B \arrow{d}{h} \\
  C \arrow{r}[swap]{k} & D
\end{tikzcd}
```

## 5. Таблицы 
```latex
\begin{table}[ht]
  \centering
  \caption{Результаты измерений}
  \label{tab:data}
  \begin{tabular}{@{} l S[table-format=3.2] S[table-format=1.3] @{}} 
    \toprule
    Образец & {Длина, мм} & {Погрешность, мм} \\
    \midrule
    №1      & 123.45      & 0.025             \\
    №2      & 130.00      & 0.030             \\
    \bottomrule
  \end{tabular}
\end{table}
```
> Используйте пакет ```siunitx``` для оформления физических величин.

## 6. Рисунки и плавающие объекты
```latex
\begin{figure}[ht]
  \centering
  \includegraphics[width=0.7\linewidth]{experiment_setup.png}
  \caption{Схема экспериментальной установки}
  \label{fig:setup}
\end{figure}
```
* Для нескольких изображений внутри:
```latex
\begin{figure}[ht]
  \centering
  \begin{subfigure}{0.45\linewidth}
    \includegraphics[width=\linewidth]{img1.png}
    \caption{Первый вариант}
  \end{subfigure}
  \quad
  \begin{subfigure}{0.45\linewidth}
    \includegraphics[width=\linewidth]{img2.png}
    \caption{Второй вариант}
  \end{subfigure}
  \caption{Сравнение вариантов}
  \label{fig:comparison}
\end{figure}
```

## 7. Ссылки и гиперссылки
* **Локальные:** ```\label{sec:intro}``` + ```\ref{sec:intro}```
* **Гиперссылки:**
```latex
Сайт документации: \href{https://www.latex-project.org/}{latex-project.org}.
```
* **Цвет и оформление** пакета ```hyperref``` настраивается через опции:
```latex
\usepackage[
  colorlinks=true,
  linkcolor=blue,
  citecolor=green,
  urlcolor=magenta
]{hyperref}
```

## 8. Библиография и цитирование
* Соберите файл ```references.bib```:
```bibtex
@article{knuth84,
  author  = {Knuth, Donald E.},
  title   = {Literate Programming},
  journal = {The Computer Journal},
  year    = 1984,
  volume  = 27,
  number  = 2,
  pages   = {97–111},
}
```
* В тексте цитируйте:
```latex
По методике~\cite{knuth84} было выполнено ...
```
* В конце документа:
```latex
\printbibliography[title=Список литературы]
```

## 9. Набор исходного кода
```latex
\begin{codewrap}
\begin{minted}[fontsize=\footnotesize]{cpp}
// Код для расчета быстрого квадратного корня.
float Q_rsqrt( float number )
{
    long i;
    float x2, y;
    const float threehalfs = 1.5F;

    x2 = number * 0.5F;
    y  = number;
    i  = * ( long * ) &y;         // evil floating point bit level hack
    i  = 0x5f3759df - ( i >> 1 ); // what the fuck?
    y  = * ( float * ) &i;
    y  = y * ( threehalfs - ( x2 * y * y ) );

    return y;
}
\end{minted}
\caption{}\label{src:quake}
\end{codewrap}
```
> Для подсветки синтаксиса на основе Pygments – пакет ```minted```.

## 10. Пользовательские команды и окружения
```latex
% Новая команда
\newcommand{\R}{\mathbb{R}}
% Новое окружение
\newenvironment{theorem}[1][]{
  \par\noindent\textbf{Теорема #1.}\itshape
}{
  \par\noindent\textbf{■}
}
```

## 11. Векторная графика с TikZ
```latex
\begin{tikzpicture}[scale=1]
  \draw[->] (0,0) -- (3,0) node[right] {$x$};
  \draw[->] (0,0) -- (0,3) node[above] {$y$};
  \draw[domain=0:2.5] plot (\x, {\x*\x}) node[right] {$y=x^2$};
\end{tikzpicture}
```

## 12. Дополнительные возможности

* Многостолбцовость: ```\begin{multicols}{2} ... \end{multicols}``` (пакет ```multicol```)
* Зноски: ```\footnote{Текст заметки}```
* Глоссарий и аббревиатуры: пакеты ```glossaries```, ```acronym```
* Индекс: пакет ```makeidx``` + ```\printindex```
* Приложения: ```\appendix``` → ```\section{Дополнительно}```

