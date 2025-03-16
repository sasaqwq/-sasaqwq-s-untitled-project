<!DOCTYPE html>
<html lang="uk">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>ViProstir</title>
  <style>
    body {
      font-family: 'Arial', sans-serif;
      margin: 0;
      background: url('https://vereta.store/wp-content/uploads/2022/08/image.jpg') no-repeat center center fixed;
      background-size: cover;
      color: #fff;
    }

    .navbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      background-color: rgba(0, 0, 0, 0.8);
      padding: 15px 30px;
      box-shadow: 0px 2px 10px rgba(0, 0, 0, 0.5);
    }

    .navbar .menu a {
      text-decoration: none;
      color: #fff;
      font-weight: bold;
      text-transform: uppercase;
      margin-right: 20px;
      font-size: 18px;
    }

    .navbar .menu a:hover {
      color: #ffdd00;
    }

    .lang-buttons button {
      background-color: #ffdd00;
      border: none;
      color: #000;
      font-size: 14px;
      font-weight: bold;
      padding: 10px 15px;
      border-radius: 5px;
      cursor: pointer;
      transition: background-color 0.3s, transform 0.2s;
    }

    .lang-buttons button:hover {
      background-color: #e6c300;
      transform: translateY(-3px);
    }

    .content-section {
      display: none;
      padding: 30px;
      margin: 20px auto;
      max-width: 800px;
      background: rgba(0, 0, 0, 0.8);
      border-radius: 10px;
      text-align: center;
      box-shadow: 0px 4px 15px rgba(0, 0, 0, 0.5);
    }

    .content-section.active {
      display: block;
    }

    #application-form {
      display: none;
      margin-top: 20px;
    }

    #application-form form {
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    #application-form label, #application-form input, #application-form textarea, #application-form button {
      margin-bottom: 10px;
    }

    #application-form input, #application-form textarea {
      width: 80%;
      padding: 10px;
      font-size: 16px;
      border: none;
      border-radius: 5px;
    }

    #application-form button {
      background-color: #ffdd00;
      padding: 10px 20px;
      font-size: 16px;
      font-weight: bold;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }

    #application-form button:hover {
      background-color: #e6c300;
    }
  </style>
  <script>
    const content = {
      uk: {
        mainTitle: "Вільний простір",
        faqTitle: "Питання та Відповіді",
        moderTitle: "MODER",
        applicationTitle: "Заявка"
      },
      en: {
        mainTitle: "Free Space",
        faqTitle: "FAQ",
        moderTitle: "MODER",
        applicationTitle: "Application"
      }
    };

    function switchLanguage(lang) {
      document.querySelectorAll('[data-lang-key]').forEach(el => {
        el.textContent = content[lang][el.dataset.langKey];
      });
    }

    function showSection(sectionId) {
      document.querySelectorAll('.content-section').forEach(sec => sec.classList.remove('active'));
      document.getElementById(sectionId).classList.add('active');
    }

    function showApplicationForm() {
      document.getElementById("application-form").style.display = "block";
    }

    function hideApplicationForm() {
      document.getElementById("application-form").style.display = "none";
    }
  </script>
</head>
<body>
  <div class="navbar">
    <div class="menu">
      <a href="#" onclick="showSection('main')"><span data-lang-key="mainTitle">Вільний простір</span></a>
      <a href="#" onclick="showSection('faq')"><span data-lang-key="faqTitle">Питання та Відповіді</span></a>
      <a href="#" onclick="showSection('application')"><span data-lang-key="applicationTitle">Заявка</span></a>
    </div>
    <div class="lang-buttons">
      <button onclick="switchLanguage('uk')">Укр</button>
      <button onclick="switchLanguage('en')">Eng</button>
    </div>
  </div>

  <main id="main" class="content-section active">
    <h1 data-lang-key="mainTitle">Вільний простір</h1>
    <p>Ласкаво просимо до нашого ViProstir!</p>
  </main>

  <section id="faq" class="content-section">
    <h2 data-lang-key="faqTitle">Питання та Відповіді</h2>
    <p>Загальні запитання та відповіді.</p>
  </section>

  <section id="application" class="content-section">
    <h2 data-lang-key="applicationTitle">Заявка</h2>
    <button onclick="showApplicationForm()">Заповнити заявку</button>
    <div id="application-form">
      <form>
        <label for="name">Ваше ім'я:</label>
        <input type="text" id="name" name="name" placeholder="Введіть ім'я" required>
        
        <label for="email">Ваш Email:</label>
        <input type="email" id="email" name="email" placeholder="Введіть Email" required>
        
        <label for="message">Ваше повідомлення:</label>
        <textarea id="message" name="message" placeholder="Введіть текст" rows="4" required></textarea>
        
        <button type="submit">Надіслати</button>
        <button type="button" onclick="hideApplicationForm()">Скасувати</button>
      </form>
    </div>
  </section>
</body>
</html>
