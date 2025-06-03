# devlog
Website
<!DOCTYPE html><html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>devlog</title>
  <style>
    body {
      margin: 0;
      background-color: #0d0d0d;
      color: #e0e0e0;
      font-family: monospace;
    }
    header {
      padding: 1rem;
      background: #1a1a1a;
      border-bottom: 1px solid #333;
      text-align: center;
      font-size: 1.2rem;
    }
    main {
      padding: 1rem;
      max-width: 700px;
      margin: auto;
    }
    nav {
      display: flex;
      gap: 1rem;
      flex-wrap: wrap;
      margin-bottom: 1rem;
    }
    nav button {
      background: #262626;
      color: #e0e0e0;
      border: 1px solid #444;
      padding: 0.5rem 1rem;
      cursor: pointer;
    }
    nav button.active {
      background: #007acc;
      color: white;
    }
    article {
      white-space: pre-wrap;
      line-height: 1.6;
    }
  </style>
</head>
<body>
  <header>📓 debug.log — мой dev-дневник</header>
  <main>
    <nav id="postList"></nav>
    <article id="content">Загружаю...</article>
  </main>  <script>
    const posts = [
      {
        id: 'day5',
        title: 'День 5: идея сайта',
        text: `Сегодня в голову пришла мысль — сделать свой сайт.
Не портфолио, а такой личный dev-дневник, куда можно кидать мысли, заметки, баги.
Простой, с тёмной темой. Пока только думаю, как начать.`
      },
      {
        id: 'day6',
        title: 'День 6: начинаю писать',
        text: `Сел писать. Делаю всё на чистом JavaScript, без фреймворков.
Создал структуру, начал с HTML и CSS.
Уже появляется основа, но пока всё выглядит как набросок.`
      },
      {
        id: 'day7',
        title: 'День 7: что-то уже работает',
        text: `Сайт уже открывается, тёмная тема готова, есть навигация.
Сделал простую систему заметок через JS. Завтра попробую JSON.`
      }
    ];

    const postList = document.getElementById('postList');
    const content = document.getElementById('content');

    function renderPost(id) {
      const post = posts.find(p => p.id === id);
      if (post) {
        content.textContent = post.text;
        document.querySelectorAll('nav button').forEach(btn => btn.classList.remove('active'));
        document.getElementById(id).classList.add('active');
      }
    }

    posts.forEach(post => {
      const btn = document.createElement('button');
      btn.textContent = post.title;
      btn.id = post.id;
      btn.onclick = () => renderPost(post.id);
      postList.appendChild(btn);
    });

    renderPost(posts[0].id);
  </script></body>
</html>
