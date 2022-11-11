---
title: "Google Authentication"
subtitle: ""
date: 2022-10-22T08:42:28+05:30
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
  - Google
categories:
  - Firebase

hiddenFromHomePage: false
hiddenFromSearch: false

summary: ""
resources:
  - name: featured-image
    src: featured-image.jpg
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

{{< youtube akbm4mD7X7U >}}

## "Login/Sign-in with firebase authentication with the help of Google"

<!--more-->

In the post below I have provided the basic HTML, CSS and JavaScript code for firebase authentication web page which looks like the above picture.

---

### HTML Code

In the HTML page don't forget to link your stylesheet and script file. In (Script) tag it's important to specify (type="module") otherwise our JavaScript won't load.

In JavaScript below provide your api key in place of YOUR_API_KEY from the project we created in firebase console.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Login Page</title>
    <link rel="stylesheet" href="login.css" />
  </head>
  <body>
    <div class="container">
      <div class="login-container">
        <h2>Login</h2>
        <div class="email-container">
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
          <input
            type="submit"
            class="submit"
            name="Submit"
            id="signUp"
            value="Sign Up"
          />
        </div>

        <h3>Or with an account:</h3>
        <div class="another-account">
          <div class="google-account">
            <img src="./image/google.png" alt="google icon" class="icon" />
            <button class="google" id="login">Sign in with Google</button>
          </div>
        </div>
      </div>
    </div>
  </body>

  <script type="module">
    // Import the functions you need from the SDKs you need
    import { initializeApp } from "https://www.gstatic.com/firebasejs/9.12.1/firebase-app.js";
    import {
      getAuth,
      GoogleAuthProvider,
      signInWithRedirect,
      getRedirectResult,
    } from "https://www.gstatic.com/firebasejs/9.12.1/firebase-auth.js";

    // TODO: Add SDKs for Firebase products that you want to use
    // https://firebase.google.com/docs/web/setup#available-libraries

    // Your web app's Firebase configuration
    const firebaseConfig = {
      apiKey: "YOUR_API_KEY",
      authDomain: "authentication-app-4d33a.firebaseapp.com",
      databaseURL:
        "https://authentication-app-4d33a-default-rtdb.firebaseio.com",
      projectId: "authentication-app-4d33a",
      storageBucket: "authentication-app-4d33a.appspot.com",
      messagingSenderId: "1028491443819",
      appId: "1:1028491443819:web:24b76bd866a3dcbef8fb2e",
    };

    // Initialize Firebase
    const app = initializeApp(firebaseConfig);
    const provider = new GoogleAuthProvider(app);
    const auth = getAuth(app);

    login.addEventListener("click", (e) => {
      signInWithRedirect(auth, provider);

      getRedirectResult(auth)
        .then((result) => {
          // This gives you a Google Access Token. You can use it to access Google APIs.
          const credential = GoogleAuthProvider.credentialFromResult(result);
          const token = credential.accessToken;

          // The signed-in user info.
          const user = result.user;
        })
        .catch((error) => {
          // Handle Errors here.
          const errorCode = error.code;
          const errorMessage = error.message;
          // The email of the user's account used.
          const email = error.customData.email;
          // The AuthCredential type that was used.
          const credential = GoogleAuthProvider.credentialFromError(error);
          // ...
        });
    });
  </script>
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

### Link To Youtube Video

[Link to Youtube Video](https://youtu.be/akbm4mD7X7U)
