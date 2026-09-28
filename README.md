# CineDeck — Assignment 2 (Advanced CSS: Flexbox & Grid)

A small multi-page movie catalog site built to practice CSS Flexbox and Grid layout techniques. Astana IT University, Software Engineering, group SE-2524.

**Live demo:** https://ramazan-se-2524.github.io/assignment2-flexbox-grid/

## Tech stack

- HTML5 (semantic tags: `header`, `nav`, `main`, `section`, `article`, `aside`, `footer`)
- CSS3 — Flexbox and CSS Grid, no frameworks or JavaScript

## Project structure

Понял, с меня всё чисто на английском, и подборки объединяю в одну — теперь 3 карточки, ровнее для сетки.

Всё работает как надо (шапка — flex, кнопки, сайдбар — просто в реальном браузере projects и sidebar встанут рядом, а не друг под другом, как обычно у моего кривого движка предпросмотра).

Создай task4/index.html и task4/styles.css.

task4/index.html
html

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CineDeck — Task 4: Portfolio</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>

  <div class="page-wrapper">

    <header class="site-header">
      <div class="logo">CineDeck</div>
      <nav class="main-nav">
        <ul class="nav-list">
          <li><a href="../index.html">Home</a></li>
          <li><a href="../task1/index.html">Cards</a></li>
          <li><a href="../task2/index.html">Grid Layout</a></li>
          <li><a href="../task3/index.html">Gallery</a></li>
          <li><a href="index.html">Portfolio</a></li>
        </ul>
      </nav>
    </header>

    <div class="main-layout">

      <section class="projects">
        <article class="project-card">
          <h3>Trending Now</h3>
          <p>The most-watched titles right now, from instant classics to this month's freshest premieres.</p>
          <button>View Collection</button>
        </article>

        <article class="project-card">
          <h3>Thrillers</h3>
          <p>Edge-of-your-seat stories that keep you guessing until the very last minute.</p>
          <button>View Collection</button>
        </article>

        <article class="project-card">
          <h3>Family Night</h3>
          <p>Feel-good picks the whole family can watch together.</p>
          <button>View Collection</button>
        </article>
      </section>

      <aside class="sidebar">
        <h3>About CineDeck</h3>
        <p>A small movie catalog and curated collections to help you pick something to watch tonight.</p>
        <ul class="sidebar-facts">
          <li><strong>Titles in catalog:</strong> 12+</li>
          <li><strong>Collections:</strong> 3</li>
          <li><strong>Updated:</strong> weekly</li>
        </ul>
      </aside>

    </div>

    <footer class="site-footer">
      <p>&copy; 2026 CineDeck — student project</p>
    </footer>

  </div>

</body>
</html>

Про пути в навбаре: task4/index.html лежит внутри папки task4, поэтому чтобы попасть в корень (lesson2/index.html) нужно сначала "выйти" на уровень выше — ../ означает именно это. А к соседним папкам (task1, task2, task3) — ../task1/index.html (выйти наверх, потом зайти в task1).

task4/styles.css
css

- {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  }

body {
font-family: 'Segoe UI', Arial, sans-serif;
background: #0b1120;
color: #e2e8f0;
}

/_ ============================================================
ВНЕШНИЙ GRID — вся страница: header / main / footer
============================================================ _/
.page-wrapper {
display: grid;
grid-template-rows: auto 1fr auto; /_ пункт 1: header/main/footer, footer всегда внизу — пункт 5 _/
min-height: 100vh;
}

/_ ============================================================
HEADER — flex-навбар (пункт 2) — это наконец Task 0!
============================================================ _/
.site-header {
display: flex;
justify-content: space-between;
align-items: center;
padding: 1rem 2rem;
background: #111827;
}

.logo {
font-size: 1.4rem;
font-weight: 700;
color: #ffffff;
}

.nav-list {
display: flex;
align-items: center;
gap: 2rem;
list-style: none;
}

.nav-list a {
color: #cbd5e1;
text-decoration: none;
}

.nav-list a:hover {
color: #7dd3fc;
}

/_ ============================================================
ВНУТРЕННИЙ GRID — main: projects слева, sidebar справа (пункт 3)
============================================================ _/
.main-layout {
display: grid;
grid-template-columns: 2fr 1fr; /_ projects шире, sidebar уже _/
gap: 1.5rem;
padding: 2rem;
max-width: 1100px;
margin: 0 auto;
width: 100%;
}

.projects {
display: flex;
flex-direction: column;
gap: 1.5rem;
}

/_ ============================================================
PROJECT CARD — flex внутри карточки (пункт 4)
============================================================ _/
.project-card {
display: flex;
flex-direction: column;
background: #111827;
border-radius: 12px;
padding: 1.5rem;
}

.project-card h3 {
margin-bottom: 0.5rem;
}

.project-card p {
color: #94a3b8;
flex: 1;
margin-bottom: 1rem;
}

.project-card button {
align-self: flex-start;
padding: 0.6rem 1.2rem;
border: none;
border-radius: 6px;
background: #7dd3fc;
color: #0b1120;
font-weight: 600;
cursor: pointer;
}

/_ ============================================================
SIDEBAR
============================================================ _/
.sidebar {
background: #111827;
border-radius: 12px;
padding: 1.5rem;
align-self: start;
}

.sidebar h3 {
margin-bottom: 0.75rem;
}

.sidebar p {
color: #94a3b8;
margin-bottom: 1rem;
}

.sidebar-facts {
list-style: none;
}

.sidebar-facts li {
padding: 0.4rem 0;
border-top: 1px solid #1e293b;
}

/_ ============================================================
FOOTER
============================================================ _/
.site-footer {
background: #111827;
color: #94a3b8;
text-align: center;
padding: 1rem 2rem;
}

Почему тут ДВА разных grid, а не один — это ключевая мысль всего задания: .page-wrapper — первый grid, три СТРОКИ (header/main/footer). .main-layout — второй, отдельный grid, ВЛОЖЕННЫЙ внутрь средней строки первого, уже с КОЛОНКАМИ (projects/sidebar). Grid внутри grid — это нормально, они друг о друге ничего не знают, каждый управляет только своими прямыми детьми.

.projects — это уже НЕ grid, а flex-direction: column — три карточки просто друг под другом. Всё остальное внутри карточки (.project-card) — тот же самый flex-приём с flex: 1 на <p>, что был в Task 1, только теперь стек вертикальный.

После того как напечатаешь и проверишь — это будет и готовый Task 0: скопируй <header class="site-header">...</header> (и CSS-блок с .site-header, .logo, .nav-list) на index.html, task1/index.html, task2/index.html, task3/index.html — так навигация станет одинаковой на всех страницах, как требовало задание с самого начала.

зачем кнопки если они не работают

Разбор жалобы на нерабочие кнопки в проекте.

Хороший вопрос — короткий честный ответ: это задание вообще не про функциональность, оно только про CSS-вёрстку (Flexbox и Grid). Кнопка здесь — это просто ещё один визуальный элемент карточки, а не работающий интерфейс.

Смотри, откуда она вообще взялась — из самого текста задания:

Task 1: "each card should include an image, title, text, and button"
Task 4: "arrange content (title, description, button)"

То есть кнопка явно требуется как элемент разметки, чтобы у тебя было что расставлять через flex/grid (заголовок сверху, текст посередине, кнопка снизу — вот что реально проверяется). Работает она или нет — вообще не тема этого задания, никакого JavaScript тут по программе курса нет.

В реальном проекте, чтобы кнопка что-то реально делала, нужно ЛИБО:

<button onclick="..."> + JavaScript-код, который выполнится по клику, ЛИБО
заменить <button> на <a href="куда-то.html">, если это просто переход на другую страницу (тогда браузер сам всё сделает, без единой строчки JS)

Раз у нас нет реального контента для "коллекции триллеров" как отдельной страницы — вешать href пока особо некуда, поэтому кнопка честно осталась декоративной. Если хочешь, чтобы она хоть куда-то вела (не обязательно для оценки, просто для красоты) — могу сделать, скажем, чтобы "View Collection" вело на ../task3/index.html (галерею постеров), раз там как раз про фильмы. Нужно, или оставляем как есть?

сделай теперь фулл read.me

Вот полный README.md — с учётом того, что все 4 задания уже готовы. Просто скопируй целиком и замени содержимое файла в корне lesson2.

markdown

# CineDeck — Assignment 2 (Advanced CSS: Flexbox & Grid)

A small multi-page movie catalog site built to practice CSS Flexbox and Grid layout techniques. Astana IT University, Software Engineering, group SE-2524.

**Live demo:** https://ramazan-se-2524.github.io/assignment2-flexbox-grid/

## Tech stack

- HTML5 (semantic tags: `header`, `nav`, `main`, `section`, `article`, `aside`, `footer`)
- CSS3 — Flexbox and CSS Grid, no frameworks or JavaScript

## Project structure

.
├── index.html # Task 0 — Navigation bar (shared header)
├── styles.css
├── task1/
│ ├── index.html # Task 1 — Card Row
│ └── styles.css
├── task2/
│ ├── index.html # Task 2 — Grid Layout (Movie Details)
│ └── styles.css
├── task3/
│ ├── index.html # Task 3 — Image Gallery
│ ├── styles.css
│ └── images/ # poster SVGs
├── task4/
│ ├── index.html # Task 4 — Portfolio Page (Flexbox + Grid combined)
│ └── styles.css
└── README.md

## Tasks overview

| #   | Task                 | Technique                | Page               |
| --- | -------------------- | ------------------------ | ------------------ |
| 0   | Navigation Bar       | Flexbox                  | `index.html`       |
| 1   | Card Row             | Flexbox                  | `task1/index.html` |
| 2   | Movie Details Layout | CSS Grid                 | `task2/index.html` |
| 3   | Poster Gallery       | CSS Grid + hover overlay | `task3/index.html` |
| 4   | Portfolio Page       | Flexbox + Grid combined  | `task4/index.html` |

## Run locally

No build step needed — just open any `index.html` in a browser, or use the Live Server extension in VS Code for auto-reload.

## Notes

Movie posters are original placeholder graphics (generated SVGs), not real film posters — used to avoid copyright issues while keeping a consistent visual style.

## Author

Ramazan Sagyngali — Astana IT University, Software Engineering, group SE-2524
GitHub: [@Ramazan-SE-2524](https://github.com/Ramazan-SE-2524)
