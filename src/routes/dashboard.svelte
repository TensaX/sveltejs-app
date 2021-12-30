<script>
    import { getAuth, onAuthStateChanged } from "firebase/auth";
    import firebaseConfig from "../firebase";  
    import {initializeApp} from 'firebase/app';

    const firebaseApp= initializeApp(firebaseConfig);
    const auth = getAuth();
    let email = undefined;
    export let uid= undefined;
    onAuthStateChanged(auth, (user) => {
    if (user) {
        // User is signed in
        email = user.email;
        uid = user.getIdToken;
        // ...
    } else {
        // User is signed out
        // ...
    }
    });

    const handleNewpost=()=>{
        window.location="http://localhost:3000/newPost";
    }

</script>

<div class="my-6 bg-gray-500 ">
    <div class=" flex items-center justify-center pt-8">
        <p>
            Welcome <strong>{email}</strong> to your dashboard!!!
        </p>
    </div>
    <div class="flex items-center justify-center mt-20 mb-10">
        <p>What do you want to do today!</p>
    </div>
    <div class="grid grid-cols-1 md:grid-cols-2 justify-items-center py-40">
        <div class="custom w-40 h-40 mx-4 rounded bg-white border-black-200 shadow-md overflow-hidden relative text-center py-16" on:click={handleNewpost}>Add a Post</div>
        <div class="custom w-40 h-40 mx-4 rounded bg-white border-black-200 shadow-md overflow-hidden relative text-center py-16"> View all my posts</div>
    </div>

</div>

<style>
    .custom{
        cursor: pointer;
    }
</style>