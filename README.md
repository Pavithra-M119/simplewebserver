# EX01 Developing a Simple Webserver
## Date:25.03.2024

## AIM:
To develop a simple webserver to serve html pages.

## DESIGN STEPS:
### Step 1: 
HTML content creation.

### Step 2:
Design of webserver workflow.

### Step 3:
Implementation using Python code.

### Step 4:
Serving the HTML pages.

### Step 5:
Testing the webserver.

## PROGRAM:
index.html:
<!DOCTYPE html>
<html lang="en">
  <head>
    {% load static %}
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link
      href="https://cdn.jsdelivr.net/npm/remixicon@3.2.0/fonts/remixicon.css"
      rel="stylesheet"
    />
    <link rel="stylesheet" href="{% static 'images/style.css' %}" />
    <title>Web Design Mastery | Responsive Portfolio</title>
  </head>
  <body>
    <nav>
      <div class="nav__content">
        <div class="logo"><a href="#">PaViThRa</a></div>
        <label for="check" class="checkbox">
          <i class="ri-menu-line"></i>
        </label>
        <input type="checkbox" name="check" id="check" />
        <ul>
          <li><a href="#">Home</a></li>
          <li><a href="#">About</a></li>
          <li><a href="#">Resume</a></li>
          <li><a href="#">Portfolio</a></li>
          <li><a href="#">Contact</a></li>
        </ul>
      </div>
    </nav>
    <section class="section">
      <div class="section__container">
        <div class="content">
          <p class="subtitle">HELLO</p>
          <h1 class="title">
            I'm <span>Pavithra<br />a</span> Student
          </h1>
          <p class="description">
            Welcome to my portfolio! I'm pavithra, a highly desired person looking to
            explore the enthralling technology and rise to eminence with all
            knowledge and skills.
          </p>
          <div class="action__btns">
            <button class="hire__me">Hire Me</button>
            <button class="portfolio">Portfolio</button>
          </div>
        </div>
        <div class="image">
          <img src="{% static 'images/pavi.jpg' %}" alt="profile" />
        </div>
      </div>
    </section>
  </body>
</html>

style.css:
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap");

:root {
  --primary-color: #a855f7;
  --primary-color-dark: #9333ea;
  --secondary-color: #ca8a04;
  --text-dark: #1f2937;
  --text-light: #6b7280;
  --extra-light: #faf5ff;
  --max-width: 1200px;
}

* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

a {
  text-decoration: none;
}

body {
  font-family: "Poppins", sans-serif;
}

nav {
  width: 100%;
  position: fixed;
  top: 0;
  left: 0;
  background-color: #ffffff;
  z-index: 99;
}

.nav__content {
  max-width: var(--max-width);
  margin: auto;
  padding: 1.5rem 1rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

nav .logo a {
  font-size: 1.5rem;
  font-weight: 600;
  color: var(--primary-color);
  transition: 0.3s;
}
nav .logo a:hover {
  color: var(--primary-color-dark);
}

nav .checkbox {
  display: none;
}

nav input {
  display: none;
}
nav .checkbox i {
  font-size: 2rem;
  color: var(--primary-color);
  cursor: pointer;
}

ul {
  display: flex;
  align-items: center;
  gap: 1rem;
  list-style: none;
  transition: left 0.3s;
}

ul li a {
  padding: 0.5rem 1rem;
  border: 2px solid transparent;
  text-decoration: none;
  font-weight: 600;
  color: var(--text-dark);
  transition: 0.3s;
}

ul li a:hover {
  border-top-color: var(--secondary-color);
  border-bottom-color: var(--secondary-color);
  color: var(--secondary-color);
}

.section {
  background-color: var(--extra-light);
}

.section__container {
  min-height: 100vh;
  max-width: var(--max-width);
  margin: auto;
  padding: 1rem;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 4rem;
}

.content {
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.subtitle {
  letter-spacing: 2px;
  color: var(--text-light);
  font-weight: 600;
  margin-bottom: 0.5rem;
}

.title {
  font-size: 2.5rem;
  font-weight: 400;
  line-height: 3rem;
  color: var(--text-dark);
  margin-bottom: 1rem;
}

.title span {
  font-weight: 600;
}

.description {
  line-height: 1.5rem;
  color: var(--text-light);
  margin-bottom: 2rem;
}

.action__btns {
  display: flex;
  gap: 1rem;
}

.action__btns button {
  font-size: 1rem;
  font-weight: 600;
  letter-spacing: 2px;
  padding: 1rem 2rem;
  outline: none;
  border: 2px solid var(--primary-color);
  border-radius: 10px;
  transition: 0.3s;
  cursor: pointer;
}

.hire__me {
  background-color: var(--primary-color);
  color: #ffffff;
}

.hire__me:hover {
  background-color: var(--primary-color-dark);
}

.portfolio {
  color: var(--primary-color);
}

.portfolio:hover {
  background-color: var(--primary-color-dark);
  color: #ffffff;
}

.image {
  display: grid;
  place-items: center;
}

.image img {
  width: min(25rem, 90%);
  border-radius: 100%;
}

@media (width < 750px) {
  nav .checkbox {
    display: block;
  }

  ul {
    position: absolute;
    width: 100%;
    height: calc(100vh - 85px);
    left: -100%;
    top: 85px;
    background-color: var(--extra-light);
    flex-direction: column;
    justify-content: center;
    gap: 3rem;
  }

  nav #check:checked ~ ul {
    left: 0;
  }

  ul li a {
    font-size: 1.25rem;
  }

  .section__container {
    padding: 10rem 1rem 5rem 1rem;
    text-align: center;
    grid-template-columns: repeat(1, 1fr);
  }

  .image {
    grid-area: 1/1/2/2;
  }

  .action__btns {
    margin: auto;
  }
}

##OUTPUT:

![alt text](<Screenshot 2024-03-27 011922.png>)
![alt text](<Screenshot 2024-03-27 012529.png>)





## RESULT:
The program for implementing simple webserver is executed successfully.
