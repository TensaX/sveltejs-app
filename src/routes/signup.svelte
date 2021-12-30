<script>
    import Input from '../components/Input.svelte';
    import Button from "../components/Button.svelte";
    import {initializeApp} from 'firebase/app';
    import { getAuth, createUserWithEmailAndPassword } from "firebase/auth";
    import firebaseConfig from "../firebase";
    import { getFirestore,collection, addDoc } from "firebase/firestore"

    let username, password;

    const firebaseApp= initializeApp(firebaseConfig);
    const auth = getAuth();
    
    const db = getFirestore();

    

    const handleClick = ()=>{
        createUserWithEmailAndPassword(auth, username, password)
    .then((userCredential) => {
        // Signed in 
        const user = userCredential.user;
        console.log("user created");
        
        try {
            const docRef = addDoc(collection(db, "users"), {
                uid: user.uid
            });
            console.log("Document written with ID: ", docRef.id);
        } 
        catch (e) {
            console.error("Error adding document: ", e);
        }
    })
    .catch((error) => {
        const errorCode = error.code;
        const errorMessage = error.message;
        alert(errorMessage);
    });
    window.location="http://localhost:3000/signin";
    }
</script>

<div class="container">
    <div>
        <h1>Create Your account</h1>
        <div>
            <form on:submit|preventDefault>
                <Input label="Your email:" bind:value={username} type="email" required />
                <Input label="Your password:" bind:value={password} type="password" required />
                <Button on:click={handleClick}>Sign up!-></Button>

            </form>
            <p>Already have an account! <a href="/signin">Sign in now!</a></p>
        </div>
    </div>
</div>

<style>
    .container{
        display: flex;
        justify-content: center;
        margin-left: 200px;
    }
    h1{
        font-size: 250%;
        font-weight: bold;
        margin: 40px 0;
    }
    p{
        margin-top: 20px;
        color: gray;
    }
    a{
        color:indigo;
    }
    a:hover{
        color:mediumblue;
        font-weight: bold;
    }
</style>