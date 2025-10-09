---
title: "Firebase: Views & Likes"
weight: 15
draft: false
description: "Learn how Blowfish integrates with Firebase to dynamically display views and likes."
slug: "firebase-views"
tags: ["firebase", "views", "likes"]
series: ["Deployment Guide"]
series_order: 15
---

To enable dynamic data retrieval on your website, we support Firebase integration. This allows you to use view count functionality in lists and articles.

1. Visit <a target="_blank" href="https://firebase.com">Firebase</a> and create an account
2. Create a new project
3. Select analytics location
4. Blowfish integrates with Firebase through Firebase-related parameters in the `params.toml` configuration file. For more details, refer to <a target="_blank" href="{{< ref "docs/configuration/#theme-parameters" >}}">this page</a>. You can find an example Firebase integration file below. Please note the parameters within the FirebaseConfig object.

```js
// Import the functions you need from the SDKs you need
import { initializeApp } from "firebase/app";
import { getAnalytics } from "firebase/analytics";
// TODO: Add SDKs for Firebase products that you want to use
// https://firebase.google.com/docs/web/setup#available-libraries

// Your web app's Firebase configuration
// For Firebase JS SDK v7.20.0 and later, measurementId is optional
const firebaseConfig = {
  apiKey: "AIzaSyB5tqlqDky77Vb4Tc4apiHV4hRZI18KGiY",
  authDomain: "blowfish-21fff.firebaseapp.com",
  projectId: "blowfish-21fff",
  storageBucket: "blowfish-21fff.appspot.com",
  messagingSenderId: "60108104191",
  appId: "1:60108104191:web:039842ebe1370698b487ca",
  measurementId: "G-PEDMYR1V0K"
};

// Initialize Firebase
const app = initializeApp(firebaseConfig);
const analytics = getAnalytics(app);
```

5. Set up Firestore - Select Build and open Firestore. Create a database and start in production mode. Choose server location and wait for deployment to complete. After startup, you need to configure rules. Simply copy and paste the content below, then click publish.
```txt
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if request.auth != null;
    }
  }
}
```
6. Enable anonymous authentication - Select Build and open Authentication. Choose Get started, click Anonymous and enable it, then save.
7. Enjoy - You can now activate the article view count and like functionality in Blowfish.