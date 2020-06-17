```

import * as firebase from "firebase/app";
import "firebase/messaging";
const initializedFirebaseApp = firebase.initializeApp({

  apiKey: "AIzaSyAKVNiyFaga6LqIJbewltvXC34zkKl4YXM",
  authDomain: "turkcell-notifications.firebaseapp.com",
  databaseURL: "https://turkcell-notifications.firebaseio.com",
  projectId: "turkcell-notifications",
  storageBucket: "turkcell-notifications.appspot.com",
  messagingSenderId: "598476896164",
  appId: "1:598476896164:web:dbd115cac9d9a0c472b331"

});
const messaging = initializedFirebaseApp.messaging();
messaging.usePublicVapidKey(
// Project Settings => Cloud Messaging => Web Push certificates
  "BAarXC0Hr36FSBJVPgm-PNecF3FINDt4lHWKaMU3QO1QBuWM8z_j3WEbveMNwiVO-CYNVOaIp8iv8vQvRm65NsE"
);
export { messaging };

```


```

  messaging.requestPermission()
    .then(async function() {
  const token = await messaging.getToken();
  console.log("Token : " + token)
    })
    .catch(function(err) {
      console.log("Unable to get permission to notify.", err);
    });
  navigator.serviceWorker.addEventListener("message", (message) => console.log(message));

```


```
firebase-messaging-sw.js

importScripts("https://www.gstatic.com/firebasejs/5.9.4/firebase-app.js");
importScripts("https://www.gstatic.com/firebasejs/5.9.4/firebase-messaging.js");
firebase.initializeApp({
	// Project Settings => Add Firebase to your web app
  messagingSenderId: "100035981643"
});
const messaging = firebase.messaging();
messaging.setBackgroundMessageHandler(function(payload) {
  const promiseChain = clients
    .matchAll({
      type: "window",
      includeUncontrolled: true
    })
    .then(windowClients => {
      for (let i = 0; i < windowClients.length; i++) {
        const windowClient = windowClients[i];
        windowClient.postMessage(payload);
      }
    })
    .then(() => {
      return registration.showNotification("my notification title");
    });
  return promiseChain;
});
self.addEventListener('notificationclick', function(event) {
  // do what you want
  // ...
});

```


