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
