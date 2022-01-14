import './App.css';
import { initializeApp } from "firebase/app";
import { GoogleAuthProvider, getAuth, signInWithPopup } from "firebase/auth";
import { useState } from 'react';

function App() {
  const firebaseConfig = {
    apiKey: "AIzaSyDcUImhpFSdLg0HVO8jjsR6_j5ZINDuB0A",
    authDomain: "fir-all-practice.firebaseapp.com",
    projectId: "fir-all-practice",
    storageBucket: "fir-all-practice.appspot.com",
    messagingSenderId: "146246442899",
    appId: "1:146246442899:web:1a1f3c5f976ce64d2e1266"
  };

  const [user, setUser] = useState({});

  const app = initializeApp(firebaseConfig);
  const provider = new GoogleAuthProvider();
  const auth = getAuth();

  const handleGoogleSignIn = () => {
    signInWithPopup(auth, provider)
      .then(result => {
        console.log(result.user)
        const { displayName, email, photoURL } = result.user;
        const loggedInUser = {
          name: displayName,
          email: email,
          photo: photoURL

        };
        setUser(loggedInUser);
      })
  }



  return (
    <div className="App">
      <button onClick={handleGoogleSignIn}>Google Sign In</button>
      {
        <div>
          <h3>{user.name}</h3>
          <p>{user.email}</p>
          <img src={user.photo} alt="" />
        </div>
      }
    </div>
  );
}

export default App;#   s i m p l e - f i r e b a s e - a u t h e n t i c a t i o n  
 