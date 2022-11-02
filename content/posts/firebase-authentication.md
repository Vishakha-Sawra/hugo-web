---
title: "Firebase Authentication"
subtitle: ""
date: 2022-10-02T09:10:18+05:30
draft: false
author: "Vishakha"
authorLink: ""
authorEmail: ""
description: ""
keywords: ""
license: ""
comment: false
weight: 0

tags:
  - Firebase
categories:
  - Firebase

hiddenFromHomePage: false
hiddenFromSearch: false

summary: ""
resources:
  - name: featured-image
    src: avatar.png
  - name: featured-image-preview
    src: featured-image-preview.jpg

toc:
  enable: true
math:
  enable: false
lightgallery: false
seo:
  images: []

repost:
  enable: true
  url: ""
# See details front matter: https://fixit.lruihao.cn/theme-documentation-content/#front-matter
---

<!-- ![Firebase Auth](/images/auth.png) -->

{{< youtube 8L6QIynk0lk>}}

## "Login/Sign-in with firebase authentication with the help of Email/Password"

<!--more-->

In the post below I have provided the basic HTML, CSS and JavaScript code for firebase authentication web page.

---

### HTML Code

In the HTML page don't forget to link your stylesheet and script file. In (Script) tag it's important to specify (type="module") otherwise our external JavaScript file won't load.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Login Page</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div class="container">
      <div class="login-container">
        <div class="email-container">
          <h2>Login</h2>
          <input
            type="text"
            class="email"
            name="email"
            id="email"
            placeholder="E-mail"
          />
          <input
            type="password"
            class="email"
            name="Password"
            id="password"
            placeholder="Your Password"
          />
          <input type="submit" name="Submit" id="signUp" value="Sign Up" />
        </div>

        <h3>Or with an account:</h3>
        <div class="google-account" id="login">
          <img src="./image/google.png" alt="google icon" class="icon" />
          <button class="google">Sign in with Google</button>
        </div>
      </div>
    </div>
  </body>
  <script type="module" src="script.js"></script>
</html>
```

---

### CSS Code

If in CSS you want to change the font-family, change it in import url and then in body or you can just remove the import url and change font-family in body.

```css
@import url("https://fonts.googleapis.com/css2?family=Open+Sans&display=swap");

* {
  box-sizing: border-box;
}

body {
  font-family: "Open Sans", "sans-serif";
  margin: 0;
  padding: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: rgba(92, 150, 249, 0.523);
  min-height: 100vh;
}

.container {
  background-color: rgba(0, 0, 0, 0.222);
  padding: 20px;
  border-radius: 7px;
  width: 50%;
  height: auto;
}

.email {
  margin: 10px 0;
  width: 100%;
  height: 30px;
  border: none;
  padding-left: 5px;
}

.email:focus {
  padding-left: 5px;
  font-size: 15px;
}

.email-container input:focus {
  outline: 1px solid black;
}

.email-container #signUp {
  width: auto;
  height: 27px;
  margin-top: 10px;
  cursor: pointer;
}

.google-account img {
  width: 25px;
  height: 25px;
}

.google-account {
  width: 98%;
  display: flex;
  background-color: #fff;
  padding: 7px;
  cursor: pointer;
}

.google-account button {
  border: none;
  background-color: #fff;
  cursor: pointer;
}
```

---

### JavaScript Code

In JavaScript provide your api key in place of YOUR_API_KEY from the project we created in firebase console.

```js
// Import the functions you need from the SDKs you need
import { initializeApp } from "https://www.gstatic.com/firebasejs/9.12.0/firebase-app.js";
import {
  getAuth,
  createUserWithEmailAndPassword,
} from "https://www.gstatic.com/firebasejs/9.12.0/firebase-auth.js";
// TODO: Add SDKs for Firebase products that you want to use
// https://firebase.google.com/docs/web/setup#available-libraries

// Your web app's Firebase configuration
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "authentication-13ca1.firebaseapp.com",
  projectId: "authentication-13ca1",
  storageBucket: "authentication-13ca1.appspot.com",
  messagingSenderId: "939650460130",
  appId: "1:939650460130:web:fb15845d8a50f0810a31bb",
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);
const auth = getAuth();

signUp.addEventListener("click", (e) => {
  var email = document.getElementById("email").value;
  var password = document.getElementById("password").value;

  createUserWithEmailAndPassword(auth, email, password)
    .then((userCredential) => {
      // Signed in
      const user = userCredential.user;
      alert("Congratulations 🥳 You are signed in!");
      // ...
    })
    .catch((error) => {
      const errorCode = error.code;
      const errorMessage = error.message;
      // ..
    });
});
```

---

### Link To Youtube Video

[Link to Youtube Video](https://youtu.be/8L6QIynk0lk)
