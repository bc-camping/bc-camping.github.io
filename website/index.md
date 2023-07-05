---
layout: default
title: Search
---

<html>
<head>
  <meta charset="utf-8">
  <title>{{ page.title }}</title>
  <style>
    /* Add your CSS styles here */
    body {
      margin: 0;
      padding: 0;
    }

    .container {
      display: flex;
      flex-direction: column;
      align-items: flex-end;
      margin-top: 10vh;
      position: relative;
    }

    .form-column {
      width: calc(100% / 4);
      display: flex;
      flex-direction: column;
      align-items: center;
      background-color: #f2f2f2;
      padding: 2em;
      margin-right: 2em;
      margin-bottom: 2em;
    }

    .search-form {
      width: 100%;
      max-width: 400px;
    }

    .search-form label {
      display: block;
      margin-bottom: 1vh;
      font-size: 2vw;
    }

    .search-form input[type="text"],
    .search-form input[type="date"] {
      padding: 2vh;
      margin-bottom: 2vh;
      width: 100%;
      font-size: 2vw;
    }

    .search-form .button-wrapper {
      display: flex;
      justify-content: center;
    }

    .search-form button[type="submit"] {
      padding: 1.5vh 3vw;
      background-color: #002b5d;
      color: #ffffff;
      font-size: 2.5vw;
      border: none;
      cursor: pointer;
    }

    .image-column {
      width: 100%;
    }

    .image-column img {
      width: 100%;
      height: auto;
      display: block;
    }

    .menu-bar {
      background-color: #002b5d;
      padding: 1em;
    }

    .menu-bar ul {
      list-style-type: none;
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
    }

    .menu-bar li {
      margin-right: 1em;
    }

    .menu-bar a {
      text-decoration: none;
      color: #ffffff;
      font-size: 1.5em;
    }
  </style>
</head>
<body>
  <div class="menu-bar">
    <ul>
      <li><a href="/">Search</a></li>
      <li><a href="/about">About</a></li>
      <li><a href="/contact">Contact Me</a></li>
    </ul>
  </div>

  <div class="container">
    <div class="form-column">
      <div class="search-form">
        <form action="/search-results" method="GET">
          <label for="address">Address:</label>
          <input type="text" id="address" name="address" required>

          <label for="start-date">Start Date:</label>
          <input type="date" id="start-date" name="start-date" required>

          <label for="end-date">End Date:</label>
          <input type="date" id="end-date" name="end-date" required>

          <div class="button-wrapper">
            <button type="submit">Search</button>
          </div>
        </form>
      </div>
    </div>

    <div class="image-column">
      <img src="background.jpg" alt="Background Image">
    </div>
  </div>
</body>
</html>
